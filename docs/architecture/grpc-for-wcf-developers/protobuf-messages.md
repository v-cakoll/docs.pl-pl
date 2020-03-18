---
title: Wiadomości Protobuf - gRPC dla programistów WCF
description: Dowiedz się, jak wiadomości Protobuf są zdefiniowane w IDL i generowane w języku C#.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147987"
---
# <a name="protobuf-messages"></a>Komunikaty Protobuf

W tej sekcji opisano sposób deklarowania komunikatów `.proto` buforu protokołu (Protobuf) w plikach. Wyjaśnia podstawowe pojęcia numerów pól i typów i patrzy na kod `protoc` C#, który generuje kompilator.

Reszta rozdziału będzie bardziej szczegółowo patrzeć na to, jak różne rodzaje danych są reprezentowane w Protobuf.

## <a name="declaring-a-message"></a>Deklarowanie wiadomości

W programie Windows Communication Foundation `Stock` (WCF) klasa dla aplikacji obrotu giełdowego może być zdefiniowana w następujący sposób w poniższym przykładzie:

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

Aby zaimplementować równoważną klasę w Protobuf, należy zadeklarować ją w `.proto` pliku. Kompilator `protoc` wygeneruje klasę .NET jako część procesu kompilacji.

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

Pierwszy wiersz deklaruje używaną wersję składni. Wersja 3 języka została wydana w 2016 roku. Jest to wersja, którą polecamy dla usług gRPC.

Wiersz `option csharp_namespace` określa obszar nazw, który ma być używany dla wygenerowanych typów C#. Ta opcja zostanie zignorowana, `.proto` gdy plik zostanie skompilowany dla innych języków. Pliki Protobuf często zawierają opcje specyficzne dla języka dla kilku języków.

Definicja `Stock` wiadomości określa cztery pola. Każdy z nich ma typ, nazwę i numer pola.

## <a name="field-numbers"></a>Numery pól

Numery pól są ważną częścią Protobuf. Są one używane do identyfikowania pól w binarnych zakodowanych danych, co oznacza, że nie można zmienić z wersji na wersję usługi. Zaletą jest to, że zgodność z poprzednimi wersjami i kompatybilność do przodu są możliwe. Klienci i usługi po prostu zignorują numery pól, o których nie wiedzą, o ile jest obsługiwana możliwość brakujących wartości.

W formacie binarnym numer pola jest łączony z identyfikatorem typu. Numery pól od 1 do 15 mogą być kodowane z ich typem jako pojedynczy bajt. Liczby od 16 do 2047 wziąć 2 bajty. Możesz iść wyżej, jeśli potrzebujesz więcej niż 2047 pól w wiadomości z jakiegokolwiek powodu. Identyfikatory pojedynczego bajtu dla numerów pól od 1 do 15 oferują lepszą wydajność, dlatego należy ich używać w najbardziej podstawowych, często używanych polach.

## <a name="types"></a>Typy

Deklaracje typów są przy użyciu natywnych typów danych skalarnych Protobuf, które zostały omówione bardziej szczegółowo w [następnej sekcji](protobuf-data-types.md). Pozostała część tego rozdziału obejmie wbudowane typy Protobuf i pokaże, jak odnoszą się one do typowych typów .NET.

> [!NOTE]
> Protobuf nie obsługuje natywnie `decimal` `double` typu, więc jest używany zamiast tego. W przypadku aplikacji, które wymagają pełnej dokładności dziesiętnej, należy zapoznać się z [sekcją dotyczącą miejsc dziesiętnych](protobuf-data-types.md#decimals) w następnej części tego rozdziału.

## <a name="the-generated-code"></a>Wygenerowany kod

Podczas tworzenia aplikacji Protobuf tworzy klasy dla każdego z komunikatów, mapowanie jego typów natywnych do typów C#. Wygenerowany `Stock` typ będzie miał następujący podpis:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

Rzeczywisty kod, który jest generowany jest znacznie bardziej skomplikowane niż to. Powodem jest to, że każda klasa zawiera cały kod niezbędny do serializacji i deserializacji się do formatu przewodu binarnego.

### <a name="property-names"></a>Nazwy właściwości

Należy zauważyć, że kompilator `PascalCase` Protobuf stosowane `snake_case` do `.proto` nazw właściwości, mimo że były one w pliku. [Protobuf styl przewodnik](https://developers.google.com/protocol-buffers/docs/style) zaleca `snake_case` użycie w definicjach wiadomości, tak aby generowanie kodu dla innych platform produkuje oczekiwane go dla ich konwencji.

>[!div class="step-by-step"]
>[Poprzedni](protocol-buffers.md)
>[następny](protobuf-data-types.md)
