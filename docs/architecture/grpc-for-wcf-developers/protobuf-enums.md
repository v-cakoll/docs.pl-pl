---
title: Wyliczenia Protobuf - gRPC dla programistów WCF
description: Dowiedz się, jak deklarować i używać wyliczeń w Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148078"
---
# <a name="protobuf-enumerations"></a>Wyliczenia Protobuf

Protobuf obsługuje typy wyliczenia. Ta obsługa była obsypana w poprzedniej sekcji, gdzie `Oneof` wyliczenie zostało użyte do określenia typu pola. Można zdefiniować własne typy wyliczenia i Protobuf skompiluje je do typów wyliczenia C#.

Ponieważ można użyć Protobuf z różnych języków, konwencje nazewnictwa dla wyliczenia różnią się od konwencji C#. Jednak generator kodu konwertuje nazwy na tradycyjny przypadek C#. Jeśli odpowiednik pascala przypadku nazwy pola zaczyna się od nazwy wyliczenia, a następnie jest usuwany.

Na przykład w poniższym wyliczeniu Protobuf pola `ACCOUNT_STATUS`są poprzedzone . Ten prefiks jest odpowiednikiem nazwy wyliczenia litery Pascal. `AccountStatus`

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Generator tworzy wyliczenie Języka C# równoważne następującemu kodzie:

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

Definicje wyliczenia protobuf *musi* mieć stałą zerową jako pierwsze pole. Podobnie jak w języku C#, można zadeklarować wiele pól o tej samej wartości. Należy jednak jawnie włączyć tę `allow_alias` opcję, korzystając z opcji w wyliczeniu:

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

Można zadeklarować wyliczenia na najwyższym `.proto` poziomie w pliku lub zagnieżdżone w definicji wiadomości. Zagnieżdżone wyliczenia — takie jak `.Types` zagnieżdżone wiadomości — będą deklarowane w klasie statycznej w wygenerowanej klasie wiadomości.

Nie ma możliwości zastosowania atrybutu [[Flags]](xref:System.FlagsAttribute) do wyliczenia wygenerowanego przez Protobuf, a Protobuf nie rozumie kombinacji wyliczenia bitowego. Spójrz na poniższy przykład:

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

Jeśli ustawisz `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`, jest serializowany jako wartość `3`całkowita . Gdy klient lub serwer próbuje deserializować wartość, nie znajdzie dopasowania w definicji wyliczenia dla `3`. Wynik będzie `Region.None`.

Najlepszym sposobem pracy z wieloma wartościami wyliczenia w `repeated` Protobuf jest użycie pola typu wyliczenia.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-any-oneof.md)
>[następny](protobuf-maps.md)
