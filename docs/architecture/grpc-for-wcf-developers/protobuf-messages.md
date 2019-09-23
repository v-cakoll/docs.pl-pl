---
title: Protobuf messages — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób komunikaty protobuf są zdefiniowane w C#IDL i generowane w.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6bb67fe3bc37fcb49c0e69b7960a00d584307b8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184205"
---
# <a name="protobuf-messages"></a>Komunikaty protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tej sekcji opisano sposób deklarowania komunikatów protobuf `.proto` w plikach, wyjaśniono podstawowe pojęcia związane z numerami pól i typami oraz wyszukiwanie C# kodu wygenerowanego przez `protoc` kompilator. Pozostała część rozdziału zawiera bardziej szczegółowe informacje na temat sposobu reprezentowania różnych typów danych w protobuf.

## <a name="declaring-a-message"></a>Deklarowanie komunikatu

W programie WCF `Stock` Klasa dla aplikacji do handlu rynkowego może być zdefiniowana jak w poniższym przykładzie:

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

Do zaimplementowania równoważnej klasy w protobuf, musi być zadeklarowany `.proto` w pliku. `protoc` Kompilator będzie generować klasę .NET jako część procesu kompilacji.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string displayName = 3;
    int32 marketId = 4;

}  
```

Pierwszy wiersz deklaruje używaną wersję składni. Wersja 3 języka została wydana w 2016 i jest zalecaną wersją dla usług gRPC Services.

Wiersz określa przestrzeń nazw, która ma być używana dla wygenerowanych C# typów. `option csharp_namespace` Ta opcja zostanie zignorowana, `.proto` gdy plik zostanie skompilowany dla innych języków. Często pliki protobuf zawierają opcje specyficzne dla języka dla kilku języków.

Definicja `Stock` komunikatu określa cztery pola, z których każdy ma typ, nazwę i numer pola.

## <a name="field-numbers"></a>Numery pól

Numery pól są ważną częścią protobuf. Są one używane do identyfikowania pól w szyfrowanych danych binarnych, co oznacza, że nie mogą ulec zmianie z wersji na wersję usługi. Zalety to zgodność z poprzednimi i progresywnymi. Klienci i usługi będą po prostu ignorować numery pól, o których się nie wie, o ile nie jest obsługiwana możliwość braku wartości.

W formacie binarnym numer pola jest połączony z identyfikatorem typu. Numery pól od 1 do 15 można zakodować ich typem jako pojedynczy bajt; liczby z 16 do 2047 mają 2 bajty. Jeśli potrzebujesz więcej niż 2047 pól w komunikacie z dowolnego powodu, możesz przejść do wyższego poziomu. Identyfikatory pojedynczych bajtów dla numerów pól od 1 do 15 oferują lepszą wydajność, dlatego należy używać ich w przypadku najbardziej podstawowych, często używanych pól.

## <a name="types"></a>Types

Deklaracje typu korzystają z natywnych typów danych skalarnych protobuf, które zostały omówione bardziej szczegółowo w [następnej sekcji](protobuf-data-types.md). Pozostała część tego rozdziału obejmuje wbudowane typy protobuf i pokazuje, w jaki sposób odnoszą się do wspólnych typów .NET.

> [!NOTE]
> Protobuf nie obsługuje `decimal` natywnie typu, dlatego w zamian użyto podwójnej precyzji. W przypadku aplikacji wymagających pełnej precyzji dziesiętnej zapoznaj się z [sekcją miejsc dziesiętnych](protobuf-data-types.md#decimals) w następnej części tego rozdziału.

## <a name="the-generated-code"></a>Wygenerowany kod

Podczas kompilowania aplikacji protobuf tworzy klasy dla poszczególnych komunikatów, mapując typy natywne na C# typy. Wygenerowany `Stock` typ będzie miał następujący podpis:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Wygenerowany kod jest znacznie bardziej skomplikowany niż ten, ponieważ każda klasa zawiera cały kod niezbędny do serializacji i deserializacji siebie w formacie sieci binarnej.

### <a name="property-names"></a>Nazwy właściwości

Należy zauważyć, że kompilator protobuf `PascalCase` zastosowany do nazw właściwości, chociaż `camelCase` znajdowały się `.proto` w pliku. Najlepiej użyć `camelCase` w definicji komunikatu, aby generowanie kodu dla innych platform było w oczekiwany sposób w przypadku ich Konwencji.

>[!div class="step-by-step"]
>[Poprzedni](protocol-buffers.md)
>[Następny](protobuf-data-types.md)
