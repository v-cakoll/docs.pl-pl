---
title: Protobuf messages — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób komunikaty protobuf są zdefiniowane w C#IDL i generowane w.
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543043"
---
# <a name="protobuf-messages"></a>Komunikaty Protobuf

W tej sekcji opisano sposób deklarowania komunikatów buforu protokołu (protobuf) w plikach `.proto`. Objaśniono podstawowe pojęcia dotyczące numerów pól i typów oraz sprawdza C# kod generowany przez kompilator `protoc`. 

Pozostała część rozdziału zawiera bardziej szczegółowe informacje na temat sposobu reprezentowania różnych typów danych w protobuf.

## <a name="declaring-a-message"></a>Deklarowanie komunikatu

W Windows Communication Foundation (WCF) Klasa `Stock` dla aplikacji handlowego rynku giełdowego może być zdefiniowana w następujący sposób:

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Aby zaimplementować równoważną klasę w protobuf, należy zadeklarować ją w pliku `.proto`. Kompilator `protoc` będzie następnie generować klasę .NET jako część procesu kompilacji.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

Pierwszy wiersz deklaruje używaną wersję składni. Wersja 3 języka została wydana w 2016. Jest to wersja, którą zalecamy dla usług gRPC Services.

Wiersz `option csharp_namespace` określa przestrzeń nazw, która ma być używana dla wygenerowanych C# typów. Ta opcja zostanie zignorowana w przypadku skompilowania pliku `.proto` dla innych języków. Pliki protobuf często zawierają opcje specyficzne dla języka dla kilku języków.

Definicja komunikatu `Stock` określa cztery pola. Każdy z nich ma typ, nazwę i numer pola.

## <a name="field-numbers"></a>Numery pól

Numery pól są ważną częścią protobuf. Są one używane do identyfikowania pól w szyfrowanych danych binarnych, co oznacza, że nie mogą ulec zmianie z wersji na wersję usługi. Zalety tej usługi to zgodność z poprzednimi wersjami i zgodność. Klienci i usługi będą po prostu ignorować numery pól, o których nie znają, tak długo, jak można obsługiwać brakujące wartości.

W formacie binarnym numer pola jest połączony z identyfikatorem typu. Numery pól od 1 do 15 można zakodować ich typem jako pojedynczy bajt. Liczby z 16 do 2 047 mają 2 bajty. Jeśli potrzebujesz więcej niż 2 047 pól w komunikacie z dowolnego powodu, możesz przejść do wyższego poziomu. Identyfikatory pojedynczych bajtów dla numerów pól od 1 do 15 oferują lepszą wydajność, dlatego należy używać ich w przypadku najbardziej podstawowych, często używanych pól.

## <a name="types"></a>Typy

Deklaracje typu korzystają z natywnych typów danych skalarnych protobuf, które zostały omówione bardziej szczegółowo w [następnej sekcji](protobuf-data-types.md). Pozostała część tego rozdziału obejmuje wbudowane typy protobuf i pokazuje, w jaki sposób odnoszą się do wspólnych typów .NET.

> [!NOTE]
> Protobuf nie obsługuje natywnie typu `decimal`, więc zamiast tego użyto `double`. W przypadku aplikacji wymagających pełnej precyzji dziesiętnej zapoznaj się z [sekcją miejsc dziesiętnych](protobuf-data-types.md#decimals) w następnej części tego rozdziału.

## <a name="the-generated-code"></a>Wygenerowany kod

Podczas kompilowania aplikacji protobuf tworzy klasy dla poszczególnych komunikatów, mapując typy natywne na C# typy. Wygenerowany typ `Stock` powinien mieć następującą sygnaturę:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Rzeczywisty wygenerowany kod jest znacznie bardziej skomplikowany niż ten. Przyczyną jest to, że każda klasa zawiera cały kod, który jest niezbędny do serializacji i deserializacji samego formatu sieci binarnej.

### <a name="property-names"></a>Nazwy właściwości

Należy zauważyć, że kompilator protobuf zastosował `PascalCase` do nazw właściwości, chociaż zostały one `snake_case` w pliku `.proto`. [Przewodnik stylu protobuf](https://developers.google.com/protocol-buffers/docs/style) zaleca używanie `snake_case` w definicjach komunikatów, dzięki czemu generowanie kodu dla innych platform daje oczekiwany przypadek dla ich Konwencji.

>[!div class="step-by-step"]
>[Poprzednie](protocol-buffers.md)
>[dalej](protobuf-data-types.md)
