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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbe7a2c4e920021c925a13ae8873124bfdb6fd67
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441947"
---
# <a name="localization"></a>Lokalizacja

Lokalizacja jest tłumaczeniem zasobów aplikacji zlokalizowane wersje w każdym kulturę, w której aplikacja będzie obsługiwać proces. Należy przejść do kroku lokalizacji, dopiero po ukończeniu [sprawdzenie](../../../docs/standard/globalization-localization/localizability-review.md) krok, aby sprawdzić, czy zglobalizowanej aplikacja jest gotowa do lokalizacji.

Aplikacja, która jest gotowy do lokalizacji jest podzielony dwóch bloków pojęć: blok, który zawiera wszystkie elementy interfejsu użytkownika i blok, który zawiera kod wykonywalny. Blok interfejsu użytkownika zawiera tylko lokalizowalne interfejsu użytkownika elementów, takich jak ciągi, komunikaty o błędach, okna dialogowe, menu, zasoby obiektów osadzonych, i tak dalej dla kultury neutralnej. Blok kodu zawiera kod w aplikacji do użycia przez wszystkie obsługiwanych kultur. Środowisko uruchomieniowe języka wspólnego obsługuje model zasobów zestawu satelickiego, która oddziela kod wykonywalny aplikacji z jej zasobami. Aby uzyskać więcej informacji dotyczących implementowania tego modelu, zobacz [zasobów na platformie .NET](../../../docs/framework/resources/index.md).

Dla każdej zlokalizowanej wersji aplikacji należy dodać nowego zestawu satelickiego, który zawiera blok interfejsu użytkownika zlokalizowany przetłumaczyć odpowiedni język dla kultury docelowej. Blok kodu dla wszystkich języków pozostają takie same. Kombinacja zlokalizowaną wersję bloku interfejsu użytkownika za pomocą bloku kodu tworzy zlokalizowanej wersji aplikacji.

[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Dostarcza Edytor zasobów formularzy Windows (Winres.exe), który pozwala na szybkie lokalizowanie formularzy Windows dla kultury docelowej. Aby dowiedzieć się, jak za pomocą tego narzędzia, zobacz [Winres.exe (Edytor zasobów Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Sprawdzenie możliwości lokalizacji](../../../docs/standard/globalization-localization/localizability-review.md)
- [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
