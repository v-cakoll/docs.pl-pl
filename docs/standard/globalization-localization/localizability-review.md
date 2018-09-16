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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b19bc78f44781923df6873ccc9720f4605731976
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678907"
---
# <a name="localizability-review"></a>Sprawdzenie możliwości lokalizacji
Przegląd możliwości zlokalizowania jest etap pośredni, w trakcie opracowywania aplikacji gotowej dla całego świata. Sprawdza, czy uniwersalnych aplikacji jest gotowy do lokalizacji i identyfikuje każdy kod lub jakiekolwiek aspekty interfejsu użytkownika, które wymagają specjalnej obsługi. Ten krok umożliwia również upewnić się, że proces lokalizacji nie wprowadza żadnych defektów funkcjonalnych w aplikacji. Gdy rozwiązano wszystkie problemy zgłoszone przez sprawdzenie, aplikacja jest gotowa do lokalizacji. W przypadku dokładne sprawdzenie, nie trzeba zmodyfikować każdy kod źródłowy w procesie lokalizacji.  
  
 Przegląd możliwości lokalizacji składa się z trzech następujące testy:  
  
-   [Zaleceń globalnych są implementowane?](#global)  
  
-   [Wrażliwość na ustawienia kulturowe funkcje są obsługiwane poprawnie?](#culture)  
  
-   [Zostały przetestowane aplikacji z danymi międzynarodowymi?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Wprowadzanie zaleceń globalnych  
 Jeśli zostały zaprojektowane i opracowane aplikacji przy użyciu lokalizacji należy pamiętać, a jeśli wykonano zaleceń omówione w [globalizacji](../../../docs/standard/globalization-localization/globalization.md) artykułu, przegląd możliwości lokalizacji w dużej mierze jest zapewnienie jakości — dostęp próbny . W przeciwnym razie na tym etapie należy przejrzeć i zaimplementować zalecenia dotyczące [globalizacji](../../../docs/standard/globalization-localization/globalization.md)i naprawiać błędy w kodzie źródłowym, które uniemożliwiają lokalizacji.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Obsługa funkcji dot. wrażliwości na ustawienia kulturowe  
 .NET Framework nie zapewnia wsparcia programowego kilka obszarów, które różnią się od kultury. W większości przypadków trzeba napisać kod niestandardowy w celu obsługi obszary funkcji, jak pokazano poniżej:  
  
-   Adresy.  
  
-   Numery telefonów.  
  
-   Rozmiary papieru.  
  
-   Jednostki miary, używane do długości, wagi, obszaru, woluminów i temperatury. Chociaż programu .NET Framework oferuje wbudowaną obsługę konwertowanie między jednostkami miary, możesz użyć <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> właściwości w celu określenia, czy danego kraju lub regionu korzysta z systemu metryki, tak jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Testowanie aplikacji  
 Zanim możesz zlokalizować aplikację, należy go przetestować, korzystając z danych w różnych językach w międzynarodowych wersjach systemu operacyjnego. Chociaż nie jest lokalizowany w tym momencie większość interfejsu użytkownika, będzie można wykrywać problemy, takie jak następujące:  
  
-   Serializowane dane nie poprawnie zdeserializować różnych wersjach systemu operacyjnego.  
  
-   Dane numeryczne, które nie odzwierciedlają konwencje bieżącej kultury. Na przykład liczby mogą być wyświetlane z separatory grup niedokładne, separatory dziesiętne i symbole walut.  
  
-   Dane daty i godziny, który nie będzie odzwierciedlał Konwencji bieżącej kultury. Na przykład numery, które reprezentują miesiąc i dzień, może pojawić się w nieprawidłowej kolejności, separatorów daty może być niepoprawna lub informacje o strefie czasowej mogą być niepoprawne.  
  
-   Zasoby, których nie można znaleźć, ponieważ nie znaleziono domyślną kulturę używaną dla swojej aplikacji.  
  
-   Ciągi, które są wyświetlane w kolejności nietypowe dla określonej kultury.  
  
-   Ciąg porównania lub porównania dla równości, które zwracają nieoczekiwane wyniki.  
  
 Jeśli już przestrzegać zaleceń globalnych, podczas tworzenia aplikacji, obsługiwane funkcje wrażliwość na ustawienia kulturowe prawidłowo i zidentyfikować i rozwiązane problemy związane z lokalizacją, które powstały podczas testowania, możesz przejść do następnego kroku [Lokalizacji](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)  
- [Lokalizacja](../../../docs/standard/globalization-localization/localization.md)  
- [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)  
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
