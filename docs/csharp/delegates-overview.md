---
title: Wprowadzenie do delegatów
description: Dowiedz się więcej na temat obiektów delegowanych, w tym temacie wprowadzono podstawowe pojęcia i opisano cele projektu języka dla obiektów delegowanych.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 84e8bf8a03bd529d9c06ad049530c19daa380065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646699"
---
# <a name="introduction-to-delegates"></a>Wprowadzenie do delegatów

[Poprzednie](delegates-events.md)

Delegaty zapewniają *późnym wiązaniu* mechanizmu na platformie .NET. Późne wiązanie oznacza, że utworzyć algorytmu, gdy obiekt wywołujący dostarcza również co najmniej jedną metodę, która implementuje część algorytmu.

Na przykład należy wziąć pod uwagę sortowanie listy gwiazdek w aplikacji związane z astronomią.
Użytkownik może sortować te gwiazdek przez ich odległości od ziemi lub wielkości gwiazdka lub ich postrzegany jasności.

W tych przypadkach metoda Sort() działa zasadniczo tak samo: Rozmieszcza elementy na liście na podstawie niektórych porównania. Kod, który porównuje dwóch gwiazdek różni się dla każdego uporządkowania sortowania.

Tego rodzaju rozwiązania zostały użyte w oprogramowaniu do połowy wieku.
C# Koncepcji delegata języka zapewnia obsługę języka pierwszej klasy i bezpieczeństwo typów wokół pojęcia.

Jak można zauważyć w dalszej części tej serii C# kod pisany algorytmy, takie jak to jest bezpiecznym typem i wykorzystuje języka i kompilatora zapewnienie typy odpowiada argumenty i zwraca typy.

## <a name="language-design-goals-for-delegates"></a>Cele projektu języka dla obiektów delegowanych

Projektanci języka wyliczane cele kilka funkcji, które ostatecznie stało się delegatów.

Zespół potrzebowała typowych konstrukcji języka, która mogłaby być używana dla dowolnego późno algorytmów powiązania. Który umożliwia deweloperom Dowiedz się, co pojęcie i używać tego samego pojęcia między wiele problemów z różnego oprogramowania.

Po drugie zespół chce się obsługiwać obu tych wywołań metody pojedynczej i multiemisji. (Obiekty delegowane multiemisji są delegatów, które ze sobą łańcucha wielu wywołań metody. Zobaczysz przykłady [dalej w tej serii](delegate-class.md).) 

Zespół chce delegatów do obsługi tych samych bezpieczeństwo typów, którzy deweloperom ze wszystkich C# konstrukcji. 

Na koniec zespół rozpoznawane, czy wzorzec zdarzeń jest jednym ze wzorców określonych, gdzie jest bardzo przydatne delegatów lub dowolnego późno algorytmu powiązania. Zespół chciała upewnij się, kod dla obiektów delegowanych stanowią podstawę dla wzorce zdarzeń platformy .NET.

Wynik o całą pracę był delegata i zdarzenia pomocy technicznej w C# i .NET. Pozostałe artykuły w tej sekcji opisano funkcje językowe, obsługa bibliotek i idiomy wspólnego, które są używane podczas pracy z delegatów.

Poznasz `delegate` generuje słowa kluczowego i jego kodu. Dowiesz się o funkcjach w `System.Delegate` klasy, a także używania tych funkcji. Dowiesz się, jak utworzyć delegatów bezpiecznego typu oraz sposób tworzenia metody, które mogą być wywoływane za pośrednictwem delegatów. Pokażemy ci również sposób pracy z delegaci i zdarzenia za pomocą wyrażenia Lambda. Zostanie wyświetlona, gdzie delegaci się jednym z bloków konstrukcyjnych dla programu LINQ. Dowiesz się, jak obiekty delegowane są podstawą wzorce zdarzeń platformy .NET i jak są one różne.

Ogólne zobaczysz, jak obiekty delegowane są integralną częścią programowania na platformie .NET i współpracę w ramach interfejsów API.

Zaczynajmy.

[Next](delegate-class.md)
