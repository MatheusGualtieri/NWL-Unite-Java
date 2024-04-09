# NWL-Unite-Java
O pass.in é uma aplicação de gestão de participantes em eventos presenciais.

A ferramenta permite que o organizador cadastre um evento e abra uma página pública de inscrição.

Os participantes inscritos podem emitir uma credencial para check-in no dia do evento.

O sistema fará um scan da credencial do participante para permitir a entrada no evento.

# Inicializar o servidor

Para inicializar, utilize o arquivo principal da aplicação: PassInApplicationTests.java

# Endpoints

A url base do projeto é : http://localhost:8080

## event

#### Cria um evento

```http
  Post /events
```

| Parâmetro   | Tipo       | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
| `title` | `string` | **Obrigatório**. O título do evento |
| `details` | `string` | **Obrigatório**. A descrição do evento |
| `maximumAttendees` | `integer` | **Obrigatório**. O número máximo de participantes do evento |

#### Retorna um evento

```http
  GET /events/${eventId}
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `eventId`      | `string` | **Obrigatório**. O ID do evento que você quer |

## attendees

#### Cria um participante

```http
  Post /events/{eventId}/attendees
```

| Parâmetro   | Tipo       | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
| `eventId`      | `string` | **Obrigatório**. O ID do evento que você quer cadastrar um participante |
| `name` | `string` | **Obrigatório**. O nome do participante |
| `email` | `string` | **Obrigatório**. O email do participante |

#### Retorna os participantes do evento

```http
  GET /events/attendees/${eventId}
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `eventId`      | `string` | **Obrigatório**. O ID do evento que você quer |

#### Retorna o crachá participante

```http
  GET /attendees/${attendeeId}/badge
```
| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `attendeeId`      | `string` | **Obrigatório**. O ID do participante que você quer |

## check-in

#### Efetua o check in de um participante

```http
  Post /attendees/{attendeeId}/check-in
```

| Parâmetro   | Tipo       | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
| `attendeeId`      | `string` | **Obrigatório**. O ID do participante que você quer |
