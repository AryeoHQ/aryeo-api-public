# Expanding Resources

Some endpoints provide a special `include` query parameter. This parameter allows the client to control the nested relations returned by an API response. For example, if a client only needs minimum information, then it may choose to omit the include parameter entirely. Or, if a client wants all possible information, then it may provide all possible values in the include parameter. This will have the side-effect of increasing the request's latency, but that may be advantageous depending on the client's use case.

> **Hint**: 📘 To see all possible values for the include parameter, use an erroneous value such as `./path?include=fake` when making a request. Then, the API will respond with all allowed include values for that endpoint.