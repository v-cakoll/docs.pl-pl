---
title: Wyliczenia protobuf — gRPC dla deweloperów WCF
description: Dowiedz się, jak deklarować wyliczenia i korzystać z nich w protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543147"
---
# <a name="protobuf-enumerations"></a>Wyliczenia Protobuf

Protobuf obsługuje typy wyliczeniowe. Ta obsługa jest obsługiwana w poprzedniej sekcji, gdzie Wyliczenie zostało użyte do określenia typu pola `Oneof`. Można zdefiniować własne typy wyliczeniowe, a protobuf będzie kompilować je do C# typów wyliczeniowych. 

Ponieważ można używać protobuf z różnymi językami, konwencje nazewnictwa dla wyliczeń różnią C# się od konwencji. Jednak generator kodu konwertuje nazwy do tradycyjnego C# przypadku. Jeśli odpowiednik w przypadku języka Pascala nazwy pola rozpoczyna się od nazwy wyliczenia, zostanie usunięty.

Na przykład w poniższym wyliczeniu protobuf pola są poprzedzone prefiksem `ACCOUNT_STATUS`. Ten prefiks jest równoważny z nazwą wyliczenia przypadku w języku Pascal, `AccountStatus`.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Generator tworzy C# odpowiednik w następującym kodzie:

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

Definicje wyliczenia protobuf *muszą* mieć stałą zero jako swoje pierwsze pole. Podobnie jak C#w programie, można zadeklarować wiele pól o tej samej wartości. Należy jednak jawnie włączyć tę opcję przy użyciu opcji `allow_alias` w wyliczeniu:

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

Jeśli ustawisz `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, zostanie ona zserializowana jako wartość całkowita `3`. Gdy klient lub serwer próbuje zdeserializować wartości, nie znajdzie dopasowania w definicji wyliczenia dla `3`. Wynik zostanie `Region.None`.

Najlepszym sposobem pracy z wieloma wartościami wyliczenia w protobuf jest użycie pola `repeated` typu wyliczeniowego.

>[!div class="step-by-step"]
>[Poprzednie](protobuf-any-oneof.md)
>[dalej](protobuf-maps.md)
