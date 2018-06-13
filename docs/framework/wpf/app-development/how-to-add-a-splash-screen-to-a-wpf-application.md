---
title: Jak dodać ekran powitalny do aplikacji WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 06d6cb7c5a5081d3b6c4979ab50e1caaa726acbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547004"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Jak dodać ekran powitalny do aplikacji WPF
W tym temacie przedstawiono sposób dodawania okno uruchamiania lub *ekranu powitalnego*, do aplikacji Windows Presentation Foundation (WPF).  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>Aby dodać obraz istniejącego jako ekran powitalny  
  
1.  Utwórz lub znaleźć obrazu, który ma być używany dla ekranu powitalnego. Można użyć dowolnego format obrazu, który jest obsługiwany przez Windows Imaging Component (WIC). Na przykład można użyć formatu BMP, GIF, JPEG, PNG lub TIFF.  
  
2.  Dodaj plik obrazu do projektu aplikacji WPF. Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
3.  W Eksploratorze rozwiązań wybierz obraz.  
  
4.  W oknie właściwości, kliknij strzałkę listy rozwijanej dla **Akcja kompilacji** właściwości.  
  
5.  Wybierz **ekranu powitalnego** z listy rozwijanej.  
  
    > [!NOTE]
    >  Jeśli nie widzisz **ekranu powitalnego** opcji, należy sprawdzić, czy używasz [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] z dodatkiem SP1 lub nowszym.  
  
6.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Obraz ekranu powitalnego zostanie wyświetlony w Centrum ekranu, a następnie stopniowo po wyświetleniu okna głównego aplikacji.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Aby usunąć ekranu powitalnego aplikacji  
  
1.  W Eksploratorze rozwiązań wybierz obraz ekranu powitalnego.  
  
2.  W oknie właściwości ustaw **Akcja kompilacji** do **Brak**.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Aby usunąć ekranu powitalnego aplikacji  
  
-   W Eksploratorze rozwiązań Usuń obraz ekranu powitalnego.  
  
-   Obraz ekranu powitalnego Wyklucz z projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SplashScreen>  
 [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
