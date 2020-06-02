---
title: Niezależne od kultury operacje na ciągach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 0db77f3e11542bb920df1e45312a72decc2a34fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279792"
---
# <a name="culture-insensitive-string-operations"></a>Niezależne od kultury operacje na ciągach

Operacje na ciągach, w których jest uwzględniana kultura, mogą okazać się przydatne w przypadku tworzenia aplikacji, które mają wyświetlać wyniki użytkownikom na podstawie kultury. Domyślnie metody uwzględniające kulturę uzyskują kulturę do użycia z <xref:System.Globalization.CultureInfo.CurrentCulture%2A> właściwości bieżącego wątku.

Należy zauważyć, że operacje na ciągach, w których jest uwzględniana kultura, nie zawsze są pożądanym zachowaniem. Używanie operacji, w których jest uwzględniana kultura, gdy wyniki powinny być niezależne od kultury, może spowodować, że kod aplikacji przestanie działać w przypadku kultur z niestandardowymi mapowaniami wielkości liter i regułami sortowania. Aby zapoznać się z przykładem, zobacz sekcję ["porównania ciągów, które używają bieżącej kultury"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) w artykule [najlepsze rozwiązania dotyczące używania ciągów](../base-types/best-practices-strings.md) .

To, czy w operacjach na ciągach powinna być uwzględniana kultura, zależy od tego, jak aplikacja używa wyników. W operacjach na ciągach, które wyświetlają wyniki użytkownikowi, zazwyczaj powinna być uwzględniana kultura. Na przykład jeśli aplikacja wyświetla posortowaną listę zlokalizowanych ciągów w polu listy, aplikacja powinna wykonać sortowanie z uwzględnieniem kultury.

W wynikach operacji na ciągach, które są używane wewnętrznie, zazwyczaj nie powinna być uwzględniana kultura. Ogólnie, jeśli aplikacja wykonuje operacje na nazwach plików, formatach trwałości lub informacjach symbolicznych, które nie są wyświetlane użytkownikowi, wyniki operacji na ciągach nie powinny ulegać zmianie w zależności od kultury. Na przykład jeśli aplikacja porównuje ciąg w celu ustalenia, czy jest on rozpoznawanym tagiem XML, w porównaniu nie powinna być uwzględniana kultura. Ponadto, jeśli decyzja dotycząca zabezpieczeń opiera się na wyniku porównania ciągów lub operacji zmiany wielkości liter, operacja powinna być niezależna od kultury, aby zapewnić, że wynik nie będzie miał wpływ na wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A> .

Bez względu na to, czy jest tworzona aplikacja zawierająca kod służący do obsługi problemów lokalizacji i globalizacji, należy pamiętać o metodach programu .NET Framework pobierających domyślnie wyniki, w których jest uwzględniana kultura. Celem tego tematu jest zilustrowanie prawidłowego sposobu używania tych metod w aplikacjach w celu uzyskania wyników, w których nie jest uwzględniana kultura.

## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](index.md)
