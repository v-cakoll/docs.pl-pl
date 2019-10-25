---
title: Wyliczenia protobuf — gRPC dla deweloperów WCF
description: Dowiedz się, jak deklarować wyliczenia i korzystać z nich w protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f18196f54caba824d7101782a88cf3bf699560d5
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846343"
---
# <a name="protobuf-enumerations"></a>Wyliczenia Protobuf

Protobuf obsługuje typy wyliczeniowe, jak pokazano w poprzedniej sekcji, w której Wyliczenie zostało użyte do określenia typu pola `oneof`. Można zdefiniować własne typy wyliczeniowe, a protobuf będzie kompilować je C# do typów wyliczeniowych. Ponieważ protobuf można używać w różnych językach, konwencje nazewnictwa dla wyliczeń różnią się C# od konwencji. Jednak generator kodu jest sprytne i konwertuje nazwy do tradycyjnego C# przypadku. Jeśli odpowiednik w przypadku języka Pascala nazwy pola rozpoczyna się od nazwy wyliczenia, zostanie usunięty.

Na przykład w tym wyliczeniu protobuf pola są poprzedzone `ACCOUNT_STATUS`, co jest równoznaczne z nazwą wyliczenia przypadku w języku Pascal: `AccountStatus`.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

W ten sposób Generator tworzy C# równoważność następującego kodu:

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Definicje wyliczenia protobuf **muszą** mieć stałą zero jako swoje pierwsze pole. Podobnie jak C#w programie, można zadeklarować wiele pól o tej samej wartości, ale należy jawnie włączyć tę opcję przy użyciu opcji`allow_alias`w wyliczeniu:

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

Wyliczenia można zadeklarować na najwyższym poziomie w pliku `.proto` lub zagnieżdżać w ramach definicji komunikatu. Wyliczenia zagnieżdżone — takie jak komunikaty zagnieżdżone — zostaną zadeklarowane w obrębie klasy statycznej `.Types` w wygenerowanej klasie komunikatów.

Nie ma sposobu zastosowania atrybutu [[flags]](xref:System.FlagsAttribute) do wyliczenia wygenerowanego przez protobuf, a protobuf nie rozpoznaje bitowych kombinacji wyliczeniowych. Zapoznaj się z poniższym przykładem:

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

Jeśli ustawisz `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, zostanie ona zserializowana jako wartość całkowita `3`. Gdy klient lub serwer próbuje zdeserializować wartości, nie znajdzie dopasowania w definicji wyliczenia dla `3`, a wynik zostanie `Region.None`.

Najlepszym sposobem pracy z wieloma wartościami wyliczenia w protobuf jest użycie pola `repeated` typu wyliczeniowego.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-any-oneof.md)
>[Następny](protobuf-maps.md)
