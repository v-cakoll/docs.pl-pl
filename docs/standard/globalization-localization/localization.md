---
title: Lokalizacja
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 89851c42570f301bee8a3eca744eb5d069347d4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120875"
---
# <a name="localization"></a>Lokalizacja

Lokalizacja jest procesem tłumaczenia zasobów aplikacji na zlokalizowane wersje dla każdej kultury, która będzie obsługiwana przez aplikację. Należy przejść do kroku lokalizacji tylko po zakończeniu kroku [Przegląd lokalizacji,](../../../docs/standard/globalization-localization/localizability-review.md) aby sprawdzić, czy zglobalizowana aplikacja jest gotowa do lokalizacji.

Aplikacja, która jest gotowa do lokalizacji jest podzielona na dwa bloki koncepcyjne: blok, który zawiera wszystkie elementy interfejsu użytkownika i blok, który zawiera kod wykonywalny. Blok interfejsu użytkownika zawiera tylko zlokalizowane elementy interfejsu użytkownika, takie jak ciągi, komunikaty o błędach, okna dialogowe, menu, zasoby obiektów osadzonych i tak dalej dla kultury neutralnej. Blok kodu zawiera tylko kod aplikacji, który ma być używany przez wszystkie obsługiwane kultury. Czas wykonywania języka wspólnego obsługuje model zasobów zestawu satelitarnego, który oddziela kod wykonywalny aplikacji z jego zasobów. Aby uzyskać więcej informacji na temat implementowania tego modelu, zobacz [Zasoby w .NET](../../../docs/framework/resources/index.md).

Dla każdej zlokalizowanej wersji aplikacji dodaj nowy zestaw satelicki, który zawiera zlokalizowany blok interfejsu użytkownika przetłumaczony na odpowiedni język dla kultury docelowej. Blok kodu dla wszystkich kultur powinny pozostać takie same. Połączenie zlokalizowanej wersji bloku interfejsu użytkownika z blokiem kodu tworzy zlokalizowaną wersję aplikacji.

Zestaw Windows Software Development Kit (SDK) dostarcza Edytor zasobów formularzy systemu Windows (Winres.exe), który umożliwia szybkie lokalizowanie formularzy systemu Windows dla kultur docelowych. Aby uzyskać informacje dotyczące korzystania z tego narzędzia, zobacz [Winres.exe (Edytor zasobów formularzy systemu Windows)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Zobacz też

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Localizability Recenzja](../../../docs/standard/globalization-localization/localizability-review.md)
- [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
