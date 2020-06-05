---
title: Dostosowywanie, które obiekty są dostępne w My
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 5245c129281bc8c7c1c6fe9215a221889380a901
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410221"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Dostosowywanie, które obiekty są dostępne w My (Visual Basic)

W tym temacie opisano, jak można kontrolować, które `My` obiekty są włączone przez ustawienie `_MYTYPE` stałej kompilacji warunkowej projektu. Zintegrowane środowisko programistyczne (IDE) programu Visual Studio zachowuje `_MYTYPE` stałą kompilacji warunkowej dla projektu w synchronizacji z typem projektu.  
  
## <a name="predefined-_mytype-values"></a>Wstępnie zdefiniowane \_ wartości MYTYPE  

Należy użyć `/define` opcji kompilatora, aby ustawić `_MYTYPE` stałą kompilacji warunkowej. Podczas określania własnej wartości dla stałej należy `_MYTYPE` ująć wartość ciągu w sekwencjach ukośników odwrotnych/cudzysłowów ( \\ "). Można na przykład użyć:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 W tej tabeli przedstawiono sposób, w jaki `_MYTYPE` stała kompilacji warunkowej jest ustawiona na dla kilku typów projektów.  
  
|Project type (Typ projektu)|\_MYTYPE wartość|  
|------------------|--------------------|  
|Biblioteka klas|Systemy|  
|Aplikacja konsoli|Konsoli|  
|Internet|Witrynę|  
|Biblioteka formantów sieci Web|"WebControl"|  
|Aplikacja systemu Windows|WindowsForms|  
|Aplikacja systemu Windows, gdy rozpoczyna się od niestandardowego`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteka formantów systemu Windows|Systemy|  
|Usługa systemu Windows|Konsoli|  
|Pusty|Ciągiem|  
  
> [!NOTE]
> Wszystkie porównania w ciągu kompilacji warunkowej są rozróżniane wielkości liter, niezależnie od sposobu `Option Compare` ustawiania instrukcji.  
  
## <a name="dependent-_my-compilation-constants"></a>Zależne \_ Moje stałe kompilacji  

Z `_MYTYPE` kolei stała Kompilacja warunkowa kontroluje wartości kilku innych `_MY` stałych kompilacji:  
  
|\_MYTYPE|\_Aplikacja|\_KOMPUTER|\_Moje formy|\_Użytkownik|\_Webwebservices|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|Konsoli|Konsoli|Systemy|Niezdefiniowane|Systemy|Prawda|  
|Celnej|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|  
|Ciągiem|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|  
|Witrynę|Niezdefiniowane|Witrynę|Fałsz|Witrynę|Fałsz|  
|"WebControl"|Niezdefiniowane|Witrynę|Fałsz|Witrynę|Prawda|  
|"Windows" lub ""|Systemy|Systemy|Niezdefiniowane|Systemy|Prawda|  
|WindowsForms|WindowsForms|Systemy|Prawda|Systemy|Prawda|  
|"WindowsFormsWithCustomSubMain"|Konsoli|Systemy|Prawda|Systemy|Prawda|  
  
 Domyślnie niezdefiniowane stałe kompilacji warunkowej są rozpoznawane jako `FALSE` . Podczas kompilowania projektu można określić wartości dla niezdefiniowanych stałych.  
  
> [!NOTE]
> Gdy `_MYTYPE` jest ustawiona na wartość "Custom", projekt zawiera `My` przestrzeń nazw, ale nie zawiera żadnych obiektów. Ustawienie `_MYTYPE` "puste" uniemożliwia jednak kompilatorowi dodanie `My` przestrzeni nazw i jej obiektów.  
  
 W tej tabeli opisano efekty wstępnie zdefiniowanych wartości `_MY` stałych kompilacji.  
  
|Stały|Znaczenie|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Włącza `My.Application` , jeśli stała to "Console", "Windows" lub "WindowsForms":<br /><br /> -Wersja "konsoli" pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> . i ma mniejszą liczbę elementów członkowskich niż wersja systemu Windows.<br />-Wersja "Windows" pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> . i ma mniejszą liczbę elementów członkowskich niż wersja "WindowsForms".<br />— Wersja "WindowsForms" `My.Application` pochodzi od <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> . Jeśli `TARGET` stała jest zdefiniowana jako "winexe", Klasa zawiera `Sub Main` metodę.|  
|`_MYCOMPUTERTYPE`|Włącza `My.Computer` , jeśli stała to "Web" lub "Windows":<br /><br /> — Wersja "Web" pochodzi od <xref:Microsoft.VisualBasic.Devices.ServerComputer> i ma mniejszą liczbę członków niż wersja "Windows".<br />-Wersja "Windows" `My.Computer` pochodzi od <xref:Microsoft.VisualBasic.Devices.Computer> .|  
|`_MYFORMS`|Włącza `My.Forms` , jeśli stała ma wartość `TRUE` .|  
|`_MYUSERTYPE`|Włącza `My.User` , jeśli stała to "Web" lub "Windows":<br /><br /> -Wersja "Web" programu `My.User` jest skojarzona z tożsamością użytkownika bieżącego żądania HTTP.<br />-Wersja "Windows" programu `My.User` jest skojarzona z bieżącym podmiotem zabezpieczeń wątku.|  
|`_MYWEBSERVICES`|Włącza `My.WebServices` , jeśli stała ma wartość `TRUE` .|  
|`_MYTYPE`|Włącza `My.Log` , `My.Request` , i `My.Response` , jeśli stała to "Web".|  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Jak My zależy od typu projektu](../development-with-my/how-my-depends-on-project-type.md)
- [Kompilacja warunkowa](../../programming-guide/program-structure/conditional-compilation.md)
- [-Definiuj (Visual Basic)](../../reference/command-line-compiler/define.md)
- [My.Forms — Obiekt](../../language-reference/objects/my-forms-object.md)
- [My.Request — Obiekt](../../language-reference/objects/my-request-object.md)
- [My.Response — Obiekt](../../language-reference/objects/my-response-object.md)
- [My.WebServices — Obiekt](../../language-reference/objects/my-webservices-object.md)
