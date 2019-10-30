---
title: Wprowadzenie do delegatów
description: Więcej informacji o delegatach w tym temacie zawierającym podstawowe koncepcje i Omówienie celów projektowania języka dla delegatów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: deff297ccce6cd14a7cd21c49638a9c6030a9996
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037404"
---
# <a name="introduction-to-delegates"></a>Wprowadzenie do delegatów

Delegaty zapewniają mechanizm *późnego wiązania* w programie .NET. Późne wiązanie oznacza, że tworzysz algorytm, w którym obiekt wywołujący dostarcza również co najmniej jedną metodę implementującą część algorytmu.

Rozważmy na przykład sortowanie listy gwiazdek w aplikacji astronomią.
Możesz posortować te gwiazdki według ich odległości od ziemi lub wielkości gwiazdki lub ich postrzeganej jasności.

We wszystkich przypadkach Metoda Sort () zasadniczo wykonuje te same czynności: układa elementy na liście na podstawie porównania. Kod, który porównuje dwie gwiazdki, różni się w zależności od kolejności sortowania.

Te rodzaje rozwiązań zostały użyte w oprogramowaniu do połowu wieku.
Koncepcja C# delegata języka zapewnia pomoc techniczną w języku pierwszej klasy i bezpieczeństwo typów wokół koncepcji.

Jak widać w dalszej części tej serii, C# kod napisany dla algorytmów, takich jak ten typ jest bezpieczny, i wykorzystuje język i kompilator, aby upewnić się, że typy pasują do argumentów i typów zwracanych.

## <a name="language-design-goals-for-delegates"></a>Cele projektowania języka dla delegatów

Projektanci języka wyliczają kilka celów funkcji, które ostatecznie stały się delegatami.

Zespół chciał wspólną konstrukcję języka, która może być używana w przypadku algorytmów późnego wiązania. Dzięki temu deweloperzy mogą uczyć się jednego koncepcji i korzystać z tego samego koncepcji przez wiele różnych problemów z oprogramowaniem.

Drugi zespół chciał obsługiwać zarówno wywołania metody pojedynczej, jak i multiemisji. (Delegaty multiemisji są delegatami, które łączą wiele wywołań metod. Zobaczysz przykłady [w dalszej części tej serii](delegate-class.md).) 

Zespół potrzebował delegatów do obsługi tego samego typu bezpieczeństwa, który deweloperzy oczekują C# od wszystkich konstrukcji. 

Na koniec zespół uznał, że wzorzec zdarzeń jest jednym określonym wzorcem, w którym delegatów lub algorytmem późnego wiązania jest bardzo użyteczny. Zespół chciał upewnić się, że kod delegatów może stanowić podstawę dla wzorca zdarzeń .NET.

Wynikiem wszystkich czynności roboczych była obsługa delegowania i zdarzeń w programie C# i .NET. Pozostałe artykuły w tej sekcji obejmują funkcje języka, obsługę biblioteki i typowe idiomy, które są używane podczas pracy z delegatami.

Dowiesz się więcej na temat słowa kluczowego `delegate` i kodu, który generuje. Dowiesz się więcej na temat funkcji w klasie `System.Delegate` i sposobu korzystania z tych funkcji. Dowiesz się, jak tworzyć bezpieczne Delegaty typu i jak tworzyć metody, które mogą być wywoływane przez delegatów. Dowiesz się również, jak korzystać z delegatów i zdarzeń przy użyciu wyrażeń lambda. Zobaczysz, gdzie Delegaty staną się jednym z bloków konstrukcyjnych dla LINQ. Dowiesz się, jak obiekty delegowane są podstawą dla wzorca zdarzeń .NET i jak się różnią.

Ogólnie, zobaczysz, jak Delegaty są integralną częścią programowania w programie .NET i pracują z interfejsami API struktury.

Zacznijmy.

[Next](delegate-class.md)
