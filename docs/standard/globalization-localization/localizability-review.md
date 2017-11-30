---
title: "Sprawdzenie możliwości lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a>Sprawdzenie możliwości lokalizacji
Sprawdzenie możliwości lokalizacji jest etap pośredni do tworzenia aplikacji gotowe. Sprawdzi, czy uniwersalnych aplikacji jest gotowy do lokalizacji i identyfikuje żadnego kodu lub aspekty interfejsu użytkownika, które wymagają specjalnej obsługi. Ten krok pozwala, upewnij się, że proces lokalizacji nie wprowadzi wad funkcjonalności do aplikacji. Jeśli zostały rozwiązane wszystkie problemy zgłoszone przez sprawdzenie, aplikacja jest gotowa do lokalizacji. W przypadku dokładne sprawdzenie, należy nie należy zmodyfikować każdy kod źródłowy podczas procesu lokalizacji.  
  
 Sprawdzenie obejmuje trzy następujące testy:  
  
-   [Zalecenia dotyczące globalizacji są implementowane?](#global)  
  
-   [Funkcje zależne od kultury są obsługiwane poprawnie?](#culture)  
  
-   [Zostały przetestowane jest aplikacji z danymi w różnych?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Wprowadzanie zaleceń globalnych  
 Jeśli zaprojektowanych i opracowanych aplikacji z lokalizacji, pamiętając, a jeśli wykonano zaleceń omówione w [globalizacji](../../../docs/standard/globalization-localization/globalization.md) artykułu, sprawdzenie przede wszystkim będzie przebieg zapewnienia jakości . W przeciwnym razie na tym etapie należy przejrzeć i zalecenia dotyczące wdrożenia [globalizacji](../../../docs/standard/globalization-localization/globalization.md)i napraw błędy w kodzie źródłowym, które uniemożliwiają lokalizacji.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Obsługa funkcji dot. wrażliwości na ustawienia kulturowe  
 .NET Framework nie ma wsparcia programowego na kilka obszarów, które różnią się przez kultury. W większości przypadków należy napisać kod niestandardowy do obsługi funkcji obszarów podobne do poniższych:  
  
-   Adresy.  
  
-   Numery telefonów.  
  
-   Rozmiarów papieru.  
  
-   Jednostki miary używane do długości, wag obszaru, woluminów i temperatury. Chociaż programu .NET Framework nie oferuje wbudowaną obsługę konwertowanie jednostki miary, możesz użyć <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> właściwości w celu określenia, czy danego kraju lub regionu korzysta z systemu metryki, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Testowanie aplikacji  
 Przed lokalizowanie aplikacji, należy przetestować go przy użyciu danych międzynarodowych na międzynarodowe wersje systemu operacyjnego. Mimo że większość funkcji interfejsu użytkownika nie jest lokalizowany na tym etapie, można wykrywać problemy, takie jak następujące:  
  
-   Dane serializowane nie deserializować prawidłowo między wersjami systemu operacyjnego.  
  
-   Dane numeryczne, które nie są widoczne konwencje bieżącej kultury. Na przykład numery mogą być wyświetlane z separatorów grup niedokładne, separatorów dziesiętnych lub symbol waluty.  
  
-   Data i godzina dane nie są widoczne konwencje bieżącej kultury. Na przykład numery, które reprezentują miesiąca i dnia mogą pojawić się w niewłaściwej kolejności, separatory daty może być niepoprawna lub informacje o strefie czasowej mogą być niepoprawne.  
  
-   Zasoby, których nie można znaleźć, ponieważ nie znaleziono domyślną kulturę dla aplikacji.  
  
-   Ciągi, które są wyświetlane w kolejności nietypowe dla określonej kultury.  
  
-   Ciąg porównań lub porównania równości, które zwracają nieoczekiwane wyniki.  
  
 Jeśli już podczas opracowywania aplikacji, a następnie zalecenia dotyczące globalizacji, obsługiwane funkcje zależne od kultury poprawnie i zidentyfikować i metod rozwiązania lokalizacji, które powstały podczas testowania, możesz przejść do następnego kroku [Lokalizacja](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizacja i globalizacja](../../../docs/standard/globalization-localization/index.md)  
 [Lokalizacja](../../../docs/standard/globalization-localization/localization.md)  
 [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
