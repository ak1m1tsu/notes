## JSON sender

```go
import (
	"bytes"
	"encoding/json"
	"net/http"
)

type JSONResponse struct {
	Data interface{} `json:"data"`
	Message string `json:"message"`
	Error string `json:"error"`
	StatusCode int `json:"status_code"`
}

func SendJSON(w http.ResponseWriter, data interface{}, message string, err string, status int) {
	w.Header().Set("Content-Type", "application/json; charset=utf-8")
	w.WriteHeader(status)
	buf := new(bytes.Buffer)
	if err := json.NewEncoder(buf).Encode(JSONResponse{Data: data, Message: message, Error: err, StatusCode: status}); err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}
	w.Write(buf.Bytes())
}
```