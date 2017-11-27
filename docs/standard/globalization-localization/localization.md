---
title: Lokalizacja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a>Lokalizacja
Lokalizacja jest proces tłumaczenie zasobów aplikacji na zlokalizowane wersje każdego kultury, która aplikacja będzie obsługiwać. Należy przejść do kroku lokalizacji, dopiero po ukończeniu [sprawdzenie](../../../docs/standard/globalization-localization/localizability-review.md) krok, aby sprawdzić, czy uniwersalnych aplikacji jest gotowa do lokalizacji.  
  
 Aplikacja jest gotowa do lokalizacji jest podzielone na dwa bloki pojęciach, blok, który zawiera wszystkie elementy interfejsu użytkownika i bloku, który zawiera kod wykonywalny. Blok interfejs użytkownika zawiera tylko Lokalizowalny interfejsu użytkownika elementów, takich jak ciągów, komunikaty o błędach, okien dialogowych, menu i zasoby osadzone, i tak dalej dla kultury neutralnej. Blok kodu zawiera kod w aplikacji mają być używane przez wszystkich obsługiwanych języków. Środowisko uruchomieniowe języka wspólnego obsługuje model zasobów zestawu satelity oddzielający kod wykonywalny aplikacji z jego zasobów. Aby uzyskać więcej informacji o implementacji tego modelu, zobacz [zasobów w aplikacjach pulpitu](../../../docs/framework/resources/index.md).  
  
 Dla każdego zlokalizowanej wersji aplikacji Dodaj nowy zestaw satelity, który zawiera blok interfejsu użytkownika zlokalizowanych przetłumaczyć odpowiedni język dla kulturze docelowej. Blok kodu dla wszystkich języków powinny być takie same. Kombinacja zlokalizowanej wersji blok interfejsu użytkownika z bloku kodu tworzy zlokalizowanej wersji aplikacji.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Dostarcza Edytor zasobów formularzy systemu Windows (Winres.exe), który pozwala na szybkie lokalizowanie formularzy systemu Windows dla docelowej kultur. Aby dowiedzieć się, jak za pomocą tego narzędzia, zobacz [Winres.exe (Edytor zasobów formularzy systemu Windows)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizacja i globalizacja](../../../docs/standard/globalization-localization/index.md)  
 [Sprawdzenie możliwości lokalizacji](../../../docs/standard/globalization-localization/localizability-review.md)  
 [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
