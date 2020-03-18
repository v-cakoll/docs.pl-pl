---
title: Sprawdzenie możliwości lokalizacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120860"
---
# <a name="localizability-review"></a>Sprawdzenie możliwości lokalizacji

Przegląd lokalizacji jest pośrednim krokiem w rozwoju aplikacji gotowej na świat. Sprawdza, czy zglobalizowana aplikacja jest gotowa do lokalizacji i identyfikuje dowolny kod lub wszelkie aspekty interfejsu użytkownika, które wymagają specjalnej obsługi. Ten krok pomaga również upewnić się, że proces lokalizacji nie wprowadzi żadnych wad funkcjonalnych do aplikacji. Po usunięciu wszystkich problemów zgłoszonych przez przegląd localizability, aplikacja jest gotowa do lokalizacji. Jeśli przegląd możliwości lokalizowania jest dokładny, nie należy modyfikować żadnego kodu źródłowego podczas procesu lokalizacji.

Przegląd lokalizacji składa się z następujących trzech kontroli:

- [Czy zalecenia dotyczące globalizacji są wdrażane?](#global)

- [Czy funkcje zależne od kultury są obsługiwane poprawnie?](#culture)

- [Czy przetestowałeś swoją aplikację na międzynarodowych danych?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Wdrażanie zaleceń dotyczących globalizacji

Jeśli zaprojektowałeś i opracowałeś aplikację z myślą o lokalizacji, a jeśli zastosowałeś się do zaleceń omówionych w artykule [Globalizacja,](../../../docs/standard/globalization-localization/globalization.md) przegląd lokalizacji będzie w dużej mierze przepustką zapewniającą jakość. W przeciwnym razie na tym etapie należy przejrzeć i zaimplementować zalecenia dotyczące [globalizacji](../../../docs/standard/globalization-localization/globalization.md) i naprawić błędy w kodzie źródłowym, które uniemożliwiają lokalizację.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Obsługa funkcji wrażliwych na kulturę

.NET nie zapewnia obsługę programową w wielu obszarach, które różnią się znacznie w zależności od kultury. W większości przypadków musisz napisać kod niestandardowy, aby obsłużyć obszary funkcji, takie jak:

- Adresy

- Numery telefonów

- Rozmiary papieru

- Jednostki miary stosowane do długości, wag, powierzchni, objętości i temperatur

   Mimo że .NET nie oferuje wbudowanej obsługi konwersji między jednostkami <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> miary, można użyć właściwości, aby określić, czy dany kraj lub region używa systemu metryk, jak pokazano w poniższym przykładzie.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Testowanie aplikacji

Przed zlokalizowaniem aplikacji należy przetestować ją przy użyciu danych międzynarodowych w międzynarodowych wersjach systemu operacyjnego. Chociaż większość interfejsu użytkownika nie zostanie zlokalizowana w tym momencie, będzie można wykryć problemy, takie jak następujące:

- Serializowane dane, które nie deserialize poprawnie w wersjach systemu operacyjnego.

- Dane liczbowe, które nie odzwierciedlają konwencji bieżącej kultury. Na przykład liczby mogą być wyświetlane z niedokładnymi separatorami grup, separatorami dziesiętnymi lub symbolami walut.

- Dane daty i godziny, które nie odzwierciedlają konwencji bieżącej kultury. Na przykład liczby reprezentujące miesiąc i dzień mogą pojawić się w niewłaściwej kolejności, separatory dat mogą być niepoprawne lub informacje o strefie czasowej mogą być nieprawidłowe.

- Zasoby, których nie można odnaleźć, ponieważ nie zidentyfikowano kultury domyślnej dla aplikacji.

- Ciągi, które są wyświetlane w nietypowej kolejności dla określonej kultury.

- Porównania ciągów lub porównania równości, które zwracają nieoczekiwane wyniki.

Jeśli podczas opracowywania aplikacji zapoznasz się z zaleceniami dotyczącymi globalizacji, poprawnie obsługiwałeś funkcje zależne od kultury oraz identyfikowano i rozwiązywano problemy z lokalizacją, które pojawiły się podczas testowania, można przejść do następnego [kroku, Lokalizacja](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Zobacz też

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Lokalizacja](../../../docs/standard/globalization-localization/localization.md)
- [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
