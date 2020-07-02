---
title: Jak dodać ekran powitalny
description: Dowiedz się, jak dodać okno uruchamiania lub ekran powitalny do aplikacji Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617963"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Jak dodać ekran powitalny do aplikacji WPF

W tym temacie pokazano, jak dodać okno uruchamiania lub *ekran powitalny*do aplikacji Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Aby dodać istniejący obraz jako ekran powitalny

1. Utwórz lub Znajdź obraz, który ma być używany na potrzeby ekranu powitalnego. Można użyć dowolnego formatu obrazu, który jest obsługiwany przez składnik Windows Imaging Component (WIC). Można na przykład użyć formatu BMP, GIF, JPEG, PNG lub TIFF.

2. Dodaj plik obrazu do projektu aplikacji WPF.

3. W **Eksplorator rozwiązań**wybierz obraz.

4. W okno Właściwości kliknij strzałkę listy rozwijanej dla właściwości **Akcja kompilacji** .

5. Wybierz pozycję **SplashScreen** z listy rozwijanej.

6. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

     Obraz ekranu powitalnego pojawia się na środku ekranu, a następnie znika po wyświetleniu okna głównego aplikacji.

## <a name="to-exclude-the-splash-screen-from-build"></a>Aby wykluczyć ekran powitalny z kompilacji

1. W **Eksplorator rozwiązań**wybierz obraz ekranu powitalnego.

2. W oknie **Właściwości** Ustaw **akcję kompilacja** na **Brak**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Aby usunąć ekran powitalny z aplikacji

W **Eksplorator rozwiązań**Usuń obraz ekranu powitalnego.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.SplashScreen>
- [Instrukcje: Dodawanie istniejących elementów do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
