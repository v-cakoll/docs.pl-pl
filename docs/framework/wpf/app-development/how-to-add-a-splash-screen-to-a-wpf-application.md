---
title: Jak dodać ekran powitalny do aplikacji WPF
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 46efa041736870c5c0f08baa321ef0dc53cacc0d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402929"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Jak dodać ekran powitalny do aplikacji WPF

W tym temacie przedstawiono sposób dodawania oknem uruchamiania lub *ekran powitalny*, do aplikacji Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Aby dodać istniejący obraz jako ekran powitalny

1.  Utwórz lub Znajdź obraz, który chcesz użyć dla ekranu powitalnego. Możesz użyć dowolnego format obrazu, który jest obsługiwany przez Windows Imaging Component (WIC). Na przykład można użyć formatu BMP, GIF, JPEG, PNG lub TIFF.

2.  Dodaj plik obrazu do projektu aplikacji WPF.

3.  W **Eksploratora rozwiązań**, wybierz obraz.

4.  W oknie dialogowym właściwości kliknij strzałkę listy rozwijanej dla **Build Action** właściwości.

5.  Wybierz **ekranu powitalnego** z listy rozwijanej.

6.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

     Obraz ekranu powitalnego pojawia się w środku ekranu, a następnie stopniowo zmienia się po wyświetleniu okna głównego aplikacji.

## <a name="to-exclude-the-splash-screen-from-build"></a>Aby wykluczyć ekran powitalny z kompilacji

1.  W **Eksploratora rozwiązań**, wybierz obraz ekranu powitalnego.

2.  W **właściwości** oknie **Build Action** do **Brak**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Aby usunąć ekran powitalny aplikacji

W **Eksploratora rozwiązań**, Usuń obraz ekranu powitalnego.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.SplashScreen>
- [Porady: Dodawanie istniejących elementów do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
