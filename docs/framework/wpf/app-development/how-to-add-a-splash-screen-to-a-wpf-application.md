---
title: 'Instrukcje: Dodawanie ekranu powitalnego do aplikacji WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947904"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Instrukcje: Dodawanie ekranu powitalnego do aplikacji WPF

W tym temacie przedstawiono sposób dodawania oknem uruchamiania lub *ekran powitalny*, do aplikacji Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Aby dodać istniejący obraz jako ekran powitalny

1. Utwórz lub Znajdź obraz, który chcesz użyć dla ekranu powitalnego. Możesz użyć dowolnego format obrazu, który jest obsługiwany przez Windows Imaging Component (WIC). Na przykład można użyć formatu BMP, GIF, JPEG, PNG lub TIFF.

2. Dodaj plik obrazu do projektu aplikacji WPF.

3. W **Eksploratora rozwiązań**, wybierz obraz.

4. W oknie dialogowym właściwości kliknij strzałkę listy rozwijanej dla **Build Action** właściwości.

5. Wybierz **ekranu powitalnego** z listy rozwijanej.

6. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

     Obraz ekranu powitalnego pojawia się w środku ekranu, a następnie stopniowo zmienia się po wyświetleniu okna głównego aplikacji.

## <a name="to-exclude-the-splash-screen-from-build"></a>Aby wykluczyć ekran powitalny z kompilacji

1. W **Eksploratora rozwiązań**, wybierz obraz ekranu powitalnego.

2. W **właściwości** oknie **Build Action** do **Brak**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Aby usunąć ekran powitalny aplikacji

W **Eksploratora rozwiązań**, Usuń obraz ekranu powitalnego.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.SplashScreen>
- [Instrukcje: Dodaj istniejące elementy do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
