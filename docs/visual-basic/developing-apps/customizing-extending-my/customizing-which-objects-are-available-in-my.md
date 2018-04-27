---
title: Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 669641a2b6ecbf988f6cad68acf52c5561b32515
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Dostosowywanie, które obiekty są dostępne w My (Visual Basic)
W tym temacie opisano, jak można kontrolować, które `My` obiekty są włączane przez ustawienie projektu `_MYTYPE` stała warunkowego kompilacji. Visual Studio programowanie środowiska IDE (Integrated) śledzi `_MYTYPE` stała kompilacja warunkowa w projekcie zsynchronizowane z typu projektu.  
  
## <a name="predefined-mytype-values"></a>_MYTYPE wstępnie zdefiniowanych wartości  
 Należy użyć `/define` opcję kompilatora, aby ustawić `_MYTYPE` stała warunkowego kompilacji. Podczas określania własne wartości `_MYTYPE` stałej, musisz ją ująć wartość ciągu w cudzysłowie ukośnik odwrotny / (\\") sekwencji. Na przykład można użyć:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 W poniższej tabeli przedstawiono co `_MYTYPE` ustawiono stała warunkowego kompilacji projektu kilka typów.  
  
|Typ projektu|Wartość _MYTYPE|  
|------------------|--------------------|  
|Biblioteka klas|"Windows"|  
|Aplikacja konsoli|"Konsola"|  
|sieć Web|"Web".|  
|Biblioteka formantów sieci Web|"WebControl"|  
|Aplikacja systemu Windows|"WindowsForms."|  
|Aplikacja systemu Windows, jeśli począwszy niestandardowe `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteka formantów systemu Windows|"Windows"|  
|Usługa systemu Windows|"Konsola"|  
|Pusty|"Pusta"|  
  
> [!NOTE]
>  Uwzględniana wielkość liter, niezależnie od tego, jak są wszystkie porównania ciągu kompilacja warunkowa `Option Compare` ustawić instrukcji.  
  
## <a name="dependent-my-compilation-constants"></a>Stałe kompilacji _MY zależne  
 `_MYTYPE` Stała kompilacja warunkowa z kolei kontrolki wartości kilka innych `_MY` stałe kompilacji:  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Konsola"|"Konsola"|"Windows"|Niezdefiniowana|"Windows"|WARTOŚĆ TRUE|  
|"Custom"|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|  
|"Pusta"|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|Niezdefiniowana|  
|"Web".|Niezdefiniowana|"Web".|FAŁSZ|"Web".|FAŁSZ|  
|"WebControl"|Niezdefiniowana|"Web".|FAŁSZ|"Web".|WARTOŚĆ TRUE|  
|"Windows" lub ""|"Windows"|"Windows"|Niezdefiniowana|"Windows"|WARTOŚĆ TRUE|  
|"WindowsForms."|"WindowsForms."|"Windows"|WARTOŚĆ TRUE|"Windows"|WARTOŚĆ TRUE|  
|"WindowsFormsWithCustomSubMain"|"Konsola"|"Windows"|WARTOŚĆ TRUE|"Windows"|WARTOŚĆ TRUE|  
  
 Domyślnie niezdefiniowanego warunkowe kompilacji stałe rozpoznać `FALSE`. Można określić wartości dla niezdefiniowanego stałe, podczas kompilowania projektu Aby zastąpić zachowanie domyślne.  
  
> [!NOTE]
>  Gdy `_MYTYPE` jest ustawiona na "Custom", projekt nie zawiera `My` przestrzeni nazw, ale nie zawiera obiektów. Jednak ustawienie `_MYTYPE` do "Pusty" zabezpiecza kompilator przed dodaniem `My` przestrzeni nazw i jej obiektów.  
  
 Poniższa tabela zawiera opis skutków wstępnie zdefiniowanych wartości `_MY` stałe kompilacji.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Włącza `My.Application`, gdy jest stała "Konsoli," Windows "lub"WindowsForms":<br /><br /> -Wersja "Konsola" pochodzi z <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. i ma mniejszą liczbę elementów członkowskich niż wersja "Windows".<br />-Wersję "Windows" pochodzi z <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>.a ma mniej elementów członkowskich niż wersja "WindowsForms".<br />-"WindowsForms" wersja `My.Application` pochodną <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Jeśli `TARGET` stała jest zdefiniowany jako "winexe", a następnie zawiera klasę `Sub Main` metody.|  
|`_MYCOMPUTERTYPE`|Włącza `My.Computer`, jeśli jest to stała jest "Web" lub "Windows":<br /><br /> -Wersja "Web" pochodzi z <xref:Microsoft.VisualBasic.Devices.ServerComputer>, i ma mniejszą liczbę elementów członkowskich niż wersja "Windows".<br />Wersja "Windows" `My.Computer` pochodną <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Umożliwia `My.Forms`, jeśli jest to stała jest `TRUE`.|  
|`_MYUSERTYPE`|Włącza `My.User`, jeśli jest to stała jest "Web" lub "Windows":<br /><br /> -"Web" wersja `My.User` jest skojarzony z tożsamością użytkownika bieżącego żądania HTTP.<br />Wersja "Windows" `My.User` jest skojarzony z wątku bieżący podmiot zabezpieczeń.|  
|`_MYWEBSERVICES`|Umożliwia `My.WebServices`, jeśli jest to stała jest `TRUE`.|  
|`_MYTYPE`|Umożliwia `My.Log`, `My.Request`, i `My.Response`, jeśli jest to stała jest "Web".|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Jak My zależy od typu projektu](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
