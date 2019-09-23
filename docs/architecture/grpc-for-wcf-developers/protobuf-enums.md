---
title: Wyliczenia protobuf — gRPC dla deweloperów WCF
description: Dowiedz się, jak deklarować wyliczenia i korzystać z nich w protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184240"
---
# <a name="protobuf-enumerations"></a>Wyliczenia protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf obsługuje typy wyliczeniowe, jak pokazano w poprzedniej sekcji, w której Wyliczenie zostało użyte do określenia typu `oneof` pola. Można zdefiniować własne typy wyliczeniowe, a protobuf będzie kompilować je C# do typów wyliczeniowych. Ponieważ protobuf można używać w różnych językach, konwencje nazewnictwa dla wyliczeń różnią się C# od konwencji. Jednak generator kodu jest sprytne i konwertuje nazwy do tradycyjnego C# przypadku. Jeśli odpowiednik w przypadku języka Pascala nazwy pola rozpoczyna się od nazwy wyliczenia, zostanie usunięty.

Na przykład w tym wyliczeniu protobuf pola są poprzedzone prefiksem, który jest odpowiednikiem nazwy wyliczenia przypadku w `ACCOUNT_STATUS`języku `AccountStatus`Pascal:.

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

Definicje wyliczenia protobuf **muszą** mieć stałą zero jako swoje pierwsze pole. Jak w C#programie, można zadeklarować wiele pól o tej samej wartości, ale należy jawnie włączyć tę opcję przy użyciu `allow_alias` opcji w wyliczeniu:

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

Wyliczenia można zadeklarować na najwyższym poziomie `.proto` pliku lub zagnieżdżać w ramach definicji wiadomości. Wyliczenia zagnieżdżone — takie jak komunikaty zagnieżdżone — zostaną zadeklarowane w obrębie `.Types` klasy statycznej w wygenerowanej klasie komunikatów.

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
  Region availableIn = 1;
}
```

Jeśli ustawisz `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`opcję, zostanie ona zserializowana jako wartość `3`całkowita. Gdy klient lub serwer próbuje zdeserializować wartości, nie znajdzie dopasowania w definicji wyliczenia dla `3` i wynik `Region.None`będzie.

Najlepszym sposobem pracy z wieloma wartościami wyliczenia w protobuf jest użycie `repeated` pola typu wyliczeniowego.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-any-oneof.md)
>[Następny](protobuf-maps.md)
