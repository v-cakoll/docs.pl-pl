---
title: Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 74be338cd6f704174d89032fb7f9e859215c2bc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843542"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
W tym temacie opisano, jak można kontrolować, które `My` obiekty są włączone, ustawiając projektu `_MYTYPE` Stała kompilacji warunkowej. Przechowuje zintegrowanego rozwoju środowiska (IDE) Visual Studio `_MYTYPE` Stała kompilacji warunkowej w projekcie w synchronizacji z typem projektu.  
  
## <a name="predefined-mytype-values"></a>_MYTYPE wstępnie zdefiniowane wartości  
 Należy użyć `/define` opcję kompilatora, aby ustawić `_MYTYPE` Stała kompilacji warunkowej. Określając wartość dla `_MYTYPE` wartością stałą, należy ująć wartość ciągu w odwróconej kreski ułamkowej/znak cudzysłowu (\\") sekwencji. Na przykład można użyć:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 W poniższej tabeli przedstawiono co `_MYTYPE` Stała kompilacji warunkowej jest ustawiona na dla kilku typów projektów.  
  
|Typ projektu|Wartość _MYTYPE|  
|------------------|--------------------|  
|Biblioteka klas|"Windows"|  
|Aplikacja konsoli|"Konsola"|  
|sieć Web|"Web"|  
|Biblioteka formantów sieci Web|"WebControl"|  
|Aplikacja Windows|"WindowsForms"|  
|Windows aplikacji, podczas uruchamiania za pomocą niestandardowego `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteka formantów Windows|"Windows"|  
|Usługa systemu Windows|"Konsola"|  
|Pusty|"Pusty"|  
  
> [!NOTE]
>  Wszystkie porównania ciągu kompilacji warunkowej uwzględniają wielkość liter, niezależnie od tego, jak `Option Compare` ustawić instrukcji.  
  
## <a name="dependent-my-compilation-constants"></a>Stałe kompilacji _MY zależne  
 `_MYTYPE` Stała kompilacji warunkowej, z kolei kontroluje wartości kilka innych `_MY` stałe kompilacji:  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Konsola"|"Konsola"|"Windows"|Niezdefiniowane|"Windows"|WARTOŚĆ TRUE|  
|"Niestandardowe"|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|  
|"Pusty"|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|Niezdefiniowane|  
|"Web"|Niezdefiniowane|"Web"|FAŁSZ|"Web"|FAŁSZ|  
|"WebControl"|Niezdefiniowane|"Web"|FAŁSZ|"Web"|WARTOŚĆ TRUE|  
|"Windows" lub ""|"Windows"|"Windows"|Niezdefiniowane|"Windows"|WARTOŚĆ TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|WARTOŚĆ TRUE|"Windows"|WARTOŚĆ TRUE|  
|"WindowsFormsWithCustomSubMain"|"Konsola"|"Windows"|WARTOŚĆ TRUE|"Windows"|WARTOŚĆ TRUE|  
  
 Domyślnie, niezdefiniowane stałe kompilacji warunkowej rozpoznać `FALSE`. Można określić wartości dla stałych Niezdefiniowany, podczas kompilowania projektu, aby zastąpić domyślne zachowanie.  
  
> [!NOTE]
>  Gdy `_MYTYPE` jest ustawiona na "Niestandardowe", projekt zawiera `My` przestrzeni nazw, ale nie zawiera obiektów. Jednak ustawienie `_MYTYPE` do "Puste" uniemożliwia kompilator Dodawanie `My` przestrzeni nazw i jej obiektów.  
  
 W tej tabeli opisano wpływ wstępnie zdefiniowane wartości `_MY` stałe kompilacji.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Włącza `My.Application`, gdy stała jest "Konsoli", Windows, "lub"WindowsForms":<br /><br /> — Wersja "Konsola" pochodzi z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. i ma mniejszą liczbę elementów członkowskich niż wersja "Windows".<br />— Wersja "Windows" pochodzi z <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>.a ma mniej elementów członkowskich niż wersja "WindowsForms".<br />— "WindowsForms" wersja `My.Application` pochodzi od klasy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Jeśli `TARGET` stała jest zdefiniowany jako "winexe", a następnie zawiera klasę `Sub Main` metody.|  
|`_MYCOMPUTERTYPE`|Włącza `My.Computer`, gdy stała jest "Web" lub "Windows":<br /><br /> — Wersja "Web" pochodzi z <xref:Microsoft.VisualBasic.Devices.ServerComputer>, i ma mniejszą liczbę elementów członkowskich niż wersja "Windows".<br />— "Windows" wersja `My.Computer` pochodzi od klasy <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Włącza `My.Forms`, gdy stała jest `TRUE`.|  
|`_MYUSERTYPE`|Włącza `My.User`, gdy stała jest "Web" lub "Windows":<br /><br /> — "Web" wersja `My.User` jest skojarzone z tożsamością użytkownika bieżącego żądania HTTP.<br />— "Windows" wersja `My.User` jest skojarzony z jednostką bieżącego wątku.|  
|`_MYWEBSERVICES`|Włącza `My.WebServices`, gdy stała jest `TRUE`.|  
|`_MYTYPE`|Włącza `My.Log`, `My.Request`, i `My.Response`, gdy stała jest "Web".|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
