---
title: Wprowadzenie do delegatów
description: Więcej informacji na temat delegatów w tym temacie omówienie, które wprowadzono podstawowe pojęcia i opisano cele projektowania język dla obiektów delegowanych.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-delegates"></a>Wprowadzenie do delegatów

[Poprzednie](delegates-events.md)

Podaj delegatów *późne wiązanie* mechanizmu programu .NET. Późne wiązanie oznacza, że można utworzyć algorytmu, gdy obiekt wywołujący dostarcza co najmniej jedną metodę, która implementuje część algorytmu.

Rozważmy na przykład listę gwiazdki w aplikacji astronomii sortowania.
Można sortować tych gwiazdek przez ich odległość od ziemi lub wielkość gwiazdy lub ich postrzegana jasność.

W takich przypadkach metody Sort() jest zasadniczo samo: Rozmieszcza elementy na liście, na podstawie niektórych porównania. Kod, który porównuje dwie gwiazdki jest różne dla każdego uporządkowania sortowania.

Tego rodzaju rozwiązań były używane w oprogramowaniu do połowy wieku.
Pojęcie delegata języka C# zapewnia obsługę języka w pierwszej klasie i bezpieczeństwo typów myślą.

Jak można zauważyć w dalszej części tej serii, tworzonego algorytmów, takich jak to kodu C# jest typu bezpieczne i korzysta z języka i kompilatora, aby upewnić się, czy typy są prawidłowe dla argumentów i zwracanych typów.

## <a name="language-design-goals-for-delegates"></a>Cele projektowania język dla obiektów delegowanych

Projektanci języka wyliczyć kilku celów dla funkcji ostatecznie stał się delegatów.

Zespół chce konstrukcję języka wspólnego można użyć dowolnego późne powiązania algorytmów. Który umożliwia deweloperom Dowiedz się, co koncepcji i użyj tego samego pojęcia na wiele problemów z różnego oprogramowania.

Po drugie zespół chciała obsługuje zarówno wywołania metody jedno- i multiemisji. (Obiekty delegowane multiemisji są delegatów gdzie wiele metod zostało połączonych ze sobą. Zobaczysz przykłady [dalej w tej serii](delegate-class.md). 

Zespół chce delegatów do obsługi tego samego typu bezpieczeństwa, który deweloperzy oczekuje od wszystkich konstrukcji języka C#. 

Na koniec zespołu rozpoznany, że wzorzec zdarzeń jest jedną z określonym wzorcem gdzie delegatów lub dowolny algorytm późne wiązanie) jest bardzo przydatne. Zespół chce upewnij się, kod delegatów stanowią podstawę dla wzorca zdarzenia platformy .NET.

Wynik wszystkich czy pracy została obsługi delegata i zdarzeń w języku C# i platformy .NET. Pozostałe artykuły w tej sekcji opisano funkcje językowe, obsługa bibliotek i idioms wspólne, które są używane podczas pracy z obiektów delegowanych.

Dowiesz się `delegate` generuje — słowo kluczowe i jego kodu. Dowiesz się o funkcjach programu `System.Delegate` klasy, a także używania tych funkcji. Dowiesz się, jak utworzyć bezpieczne obiektów delegowanych typu i Tworzenie metody, które mogą być wywoływane za pośrednictwem obiektów delegowanych. Ponadto dowiesz się, jak do pracy z delegaci i zdarzenia za pomocą wyrażenia Lambda. Zostanie wyświetlony, gdy delegatów się jeden z bloków konstrukcyjnych dla LINQ. Dowiesz się, jak delegatów stanowią podstawę dla wzorca zdarzenia platformy .NET i jak są różne.

Ogólne zobaczysz, jak obiekty delegowane są integralną częścią programowania w programie .NET i Praca z framework interfejsów API.

Zacznijmy od początku.

[Next](delegate-class.md)
