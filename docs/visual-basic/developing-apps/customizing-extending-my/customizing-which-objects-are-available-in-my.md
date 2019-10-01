---
title: Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: caddad463f7c525c8b715d70f49bf8bebcc7cfbd
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701263"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Dostosowywanie, które obiekty są dostępne w My (Visual Basic)

W tym temacie opisano, jak można kontrolować, które obiekty `My` są włączane przez ustawienie stałej kompilacji warunkowej @no__t dla projektu. Zintegrowane środowisko programistyczne (IDE) programu Visual Studio utrzymuje stałą `_MYTYPE`, aby projekt był synchronizowany z typem projektu.  
  
## <a name="predefined-_mytype-values"></a>Wstępnie zdefiniowane wartości \_MYTYPE  

Należy użyć opcji kompilatora `/define`, aby ustawić stałą kompilacji warunkowej `_MYTYPE`. Podczas określania własnej wartości dla stałej `_MYTYPE` należy ująć wartość ciągu w sekwencjach ukośników odwrotnych/cudzysłowów (\\). Można na przykład użyć:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 W tej tabeli przedstawiono wartość stałej kompilacji warunkowej `_MYTYPE` dla kilku typów projektów.  
  
|Typ projektu|@no__t — wartość 0MYTYPE|  
|------------------|--------------------|  
|Biblioteka klas|Systemy|  
|Aplikacja konsoli|Konsoli|  
|sieć Web|Witrynę|  
|Biblioteka formantów sieci Web|"WebControl"|  
|Aplikacja systemu Windows|WindowsForms|  
|Aplikacja systemu Windows, podczas uruchamiania z niestandardowym `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteka formantów systemu Windows|Systemy|  
|Usługa systemu Windows|Konsoli|  
|Pusty|Ciągiem|  
  
> [!NOTE]
> Wszystkie porównania w ciągu kompilacji warunkowej są rozróżniane wielkości liter, niezależnie od sposobu ustawiania instrukcji `Option Compare`.  
  
## <a name="dependent-_my-compilation-constants"></a>@No__t — stałe kompilacji 0MY  

Z kolei `_MYTYPE` stała Kompilacja warunkowa kontroluje wartości kilku innych `_MY` dla stałych kompilacji:  
  
|@no__t — 0MYTYPE|@no__t — 0MYAPPLICATIONTYPE|@no__t — 0MYCOMPUTERTYPE|@no__t — 0MYFORMS|@no__t — 0MYUSERTYPE|@no__t — 0MYWEBSERVICES|  
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
> Gdy `_MYTYPE` jest ustawiona na wartość "Custom", projekt zawiera przestrzeń nazw `My`, ale nie zawiera żadnych obiektów. Ustawienie wartości `_MYTYPE` na wartość "puste" uniemożliwia kompilatorowi dodanie przestrzeni nazw `My` i jego obiektów.  
  
 W tej tabeli opisano efekty wstępnie zdefiniowanych wartości stałych kompilacji `_MY`.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Włącza `My.Application`, jeśli stała to "konsola", "Windows" lub "WindowsForms":<br /><br /> — Wersja "konsoli" pochodzi z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. i ma mniejszą liczbę elementów członkowskich niż wersja systemu Windows.<br />-Wersja "Windows" pochodzi z @no__t -0. i ma mniejszą liczbę elementów członkowskich niż wersja "WindowsForms".<br />-Wersja "WindowsForms" `My.Application` pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Jeśli stała `TARGET` jest zdefiniowana jako "winexe", Klasa zawiera metodę `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Włącza `My.Computer`, jeśli stała to "Web" lub "Windows":<br /><br /> -Wersja "Web" pochodzi od <xref:Microsoft.VisualBasic.Devices.ServerComputer> i ma mniejszą liczbę członków niż wersja "Windows".<br />-Wersja "Windows" `My.Computer` pochodzi od <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Włącza `My.Forms`, jeśli stała jest `TRUE`.|  
|`_MYUSERTYPE`|Włącza `My.User`, jeśli stała to "Web" lub "Windows":<br /><br /> -Wersja "Web" `My.User` jest skojarzona z tożsamością użytkownika bieżącego żądania HTTP.<br />-Wersja "Windows" `My.User` jest skojarzona z bieżącym podmiotem zabezpieczeń wątku.|  
|`_MYWEBSERVICES`|Włącza `My.WebServices`, jeśli stała jest `TRUE`.|  
|`_MYTYPE`|Włącza `My.Log`, `My.Request` i `My.Response`, jeśli stała to "Web".|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
