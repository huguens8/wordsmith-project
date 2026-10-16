# Étape 1 : compiler
FROM golang AS build
WORKDIR /app
COPY dispatcher.go .
RUN CGO_ENABLED=0 go build dispatcher.go

# Étape 2 : image finale, vide au départ
FROM scratch
COPY --from=build /app/dispatcher /
COPY static /static
EXPOSE 80
CMD ["/dispatcher"]