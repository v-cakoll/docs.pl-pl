---
title: Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: bb3f8eb2e8b1cf5bce364fc4b3ce0587769bb5f9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775209"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Dostosowywanie, które obiekty są dostępne w My (Visual Basic)

W tym temacie opisano, jak można kontrolować, które obiekty `My` są włączane przez ustawienie stałej kompilacji warunkowej `_MYTYPE` projektu. Zintegrowane środowisko programistyczne (IDE) programu Visual Studio utrzymuje `_MYTYPE` stałą kompilacji warunkowej dla projektu w synchronizacji z typem projektu.  
  
## <a name="predefined-_mytype-values"></a>Wstępnie zdefiniowane wartości \_MYTYPE  

Należy użyć opcji kompilatora `/define`, aby ustawić stałą `_MYTYPE` warunkowo. Podczas określania własnej wartości stałej `_MYTYPE` należy ująć wartość ciągu w sekwencjach ukośników odwrotnych/cudzysłowów (\\ "). Można na przykład użyć:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 W tej tabeli przedstawiono sposób, w jaki `_MYTYPE` stała kompilacji warunkowej jest ustawiona na dla kilku typów projektów.  
  
|Typ projektu|wartość \_MYTYPE|  
|------------------|--------------------|  
|Biblioteka klas|Systemy|  
|Aplikacja konsoli|Konsoli|  
|sieć Web|Witrynę|  
|Biblioteka formantów sieci Web|"WebControl"|  
|Aplikacja systemu Windows|WindowsForms|  
|Aplikacja systemu Windows, która rozpoczyna się od `Sub Main` niestandardowego|"WindowsFormsWithCustomSubMain"|  
|Biblioteka formantów systemu Windows|Systemy|  
|Usługa systemu Windows|Konsoli|  
|Pusty|Ciągiem|  
  
> [!NOTE]
> We wszystkich porównaniach w ciągu kompilacji warunkowej jest rozróżniana wielkość liter, niezależnie od sposobu ustawiania instrukcji `Option Compare`.  
  
## <a name="dependent-_my-compilation-constants"></a>Stałe kompilacji \_MY zależne  

Z kolei `_MYTYPE` stała Kompilacja warunkowa kontroluje wartości kilku innych `_MY` stałych kompilacji:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Konsoli|Konsoli|Systemy|definicji|Systemy|OZNACZA|  
|Celnej|definicji|definicji|definicji|definicji|definicji|  
|Ciągiem|definicji|definicji|definicji|definicji|definicji|  
|Witrynę|definicji|Witrynę|FAŁSZ|Witrynę|FAŁSZ|  
|"WebControl"|definicji|Witrynę|FAŁSZ|Witrynę|OZNACZA|  
|"Windows" lub ""|Systemy|Systemy|definicji|Systemy|OZNACZA|  
|WindowsForms|WindowsForms|Systemy|OZNACZA|Systemy|OZNACZA|  
|"WindowsFormsWithCustomSubMain"|Konsoli|Systemy|OZNACZA|Systemy|OZNACZA|  
  
 Domyślnie niezdefiniowane stałe kompilacji warunkowej rozwiązują `FALSE`. Podczas kompilowania projektu można określić wartości dla niezdefiniowanych stałych.  
  
> [!NOTE]
> Gdy `_MYTYPE` jest ustawiona na wartość "Custom", projekt zawiera `My` przestrzeni nazw, ale nie zawiera żadnych obiektów. Ustawienie `_MYTYPE` na wartość "Empty" uniemożliwia jednak kompilatorowi dodanie przestrzeni nazw `My` i jej obiektów.  
  
 W tej tabeli opisano efekty wstępnie zdefiniowanych wartości stałych kompilacji `_MY`.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Włącza `My.Application`, jeśli stała to "konsola", "Windows" lub "WindowsForms":<br /><br /> -Wersja "konsoli" pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. i ma mniejszą liczbę elementów członkowskich niż wersja systemu Windows.<br />-Wersja "Windows" pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>. i ma mniejszą liczbę elementów członkowskich niż wersja "WindowsForms".<br />-Wersja "WindowsForms" `My.Application` pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Jeśli stała `TARGET` jest zdefiniowana jako "winexe", Klasa zawiera metodę `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Włącza `My.Computer`, jeśli stała to "Web" lub "Windows":<br /><br /> -Wersja "Web" pochodzi od <xref:Microsoft.VisualBasic.Devices.ServerComputer> i ma mniejszą liczbę członków niż wersja "Windows".<br />— Wersja "Windows" `My.Computer` pochodzi od <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Włącza `My.Forms`, jeśli stała jest `TRUE`.|  
|`_MYUSERTYPE`|Włącza `My.User`, jeśli stała to "Web" lub "Windows":<br /><br /> — Wersja "Web" `My.User` jest skojarzona z tożsamością użytkownika bieżącego żądania HTTP.<br />-Wersja "Windows" `My.User` jest skojarzona z bieżącym podmiotem zabezpieczeń wątku.|  
|`_MYWEBSERVICES`|Włącza `My.WebServices`, jeśli stała jest `TRUE`.|  
|`_MYTYPE`|Włącza `My.Log`, `My.Request` i `My.Response`, jeśli stała to "Web".|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-Definiuj (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
