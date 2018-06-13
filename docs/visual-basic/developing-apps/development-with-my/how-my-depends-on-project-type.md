---
title: Jak My zależy od typu projektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: d196309bb2780db757515bd6ba1927c5821e2475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592083"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Jak My zależy od typu projektu (Visual Basic)
`My` przedstawia tylko te obiekty, które są wymagane przez typu określonego projektu. Na przykład `My.Forms` obiekt jest dostępny w aplikacji formularzy systemu Windows, ale nie jest dostępna w aplikacji konsoli. W tym temacie opisano, które `My` obiekty są dostępne w różnych typach projektów.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Moje Windows w aplikacji i witryn sieci Web  
 `My` przedstawia tylko obiekty, które są przydatne do bieżącego typu projektu. Pomija ją obiektów, które nie mają zastosowania. Na przykład poniższy obraz przedstawia `My` model obiektów w projekcie formularzy systemu Windows.  
  
 ![Kształt Moje w aplikacji formularzy systemu Windows](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 W projektach witryny sieci Web `My` uwidacznia obiekty, które są istotne dla deweloperów sieci Web (takie jak `My.Request` i `My.Response` obiektów) podczas pomijanie obiektów, które nie są istotne (takich jak `My.Forms` obiektu). Poniższy obraz przedstawia `My` model obiektów w projektach witryny sieci Web:  
  
 ![Kształt Moje w aplikacji sieci Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Szczegóły projektu  
 W poniższej tabeli przedstawiono którego `My` obiekty są domyślnie włączone dla osiem typy projektów: Windows aplikacji, klasy biblioteki aplikacji konsoli, systemu Windows Biblioteka kontrolek, sieci Web biblioteki formantu, systemu Windows usługi, pusty i witryny sieci Web.  
  
 Istnieją trzy wersje `My.Application` obiektu, dwie wersje `My.Computer` obiektu, a dwie wersje `My.User` obiekt; szczegółowe informacje o te wersje są podane w przypisach pod tabelą.  
  
|Mój obiekt|Aplikacja systemu Windows|Biblioteka klas|Aplikacja konsoli|Biblioteka formantów systemu Windows|Biblioteka formantów sieci Web|Usługa systemu Windows|Pusty|Witryna sieci Web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Tak** <sup>1</sup>|**Tak** <sup>2</sup>|**Tak** <sup>3</sup>|**Tak** <sup>2</sup>|Nie|**Tak** <sup>3</sup>|Nie|Nie|  
|`My.Computer`|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>5</sup>|**Tak** <sup>4</sup>|Nie|**Tak** <sup>5</sup>|  
|`My.Forms`|**Tak**|Nie|Nie|**Tak**|Nie|Nie|Nie|Nie|  
|`My.Log`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Tak**|  
|`My.Request`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Tak**|  
|`My.Resources`|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|Nie|Nie|  
|`My.Response`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Tak**|  
|`My.Settings`|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|Nie|Nie|  
|`My.User`|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>7</sup>|**Tak** <sup>6</sup>|Nie|**Tak** <sup>7</sup>|  
|`My.WebServices`|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|**Tak**|Nie|Nie|  
  
 <sup>1</sup> wersji formularzy systemu Windows `My.Application`. Wersja konsoli jest pochodną (patrz Uwaga 3); dodaje obsługę interakcji z aplikacji systemu windows oraz udostępnia model aplikacji Visual Basic.  
  
 <sup>2</sup> wersji biblioteki `My.Application`. Zapewnia podstawowe funkcje wymagane przez aplikację: zawiera elementy członkowskie zapisu w dzienniku aplikacji i uzyskiwanie dostępu do informacji o aplikacji.  
  
 <sup>3</sup> wersji konsoli `My.Application`. Pochodzi z wersji biblioteki (patrz Uwaga 2), a dodatkowe elementy członkowskie są dodawane do uzyskiwania dostępu do argumentów wiersza polecenia i informacje dotyczące wdrażania ClickOnce aplikacji.  
  
 <sup>4</sup> wersji systemu Windows `My.Computer`. Wersja serwera jest pochodną (patrz Uwaga 5) oraz zapewnia dostęp do obiektów przydatna na komputerze klienckim, takich jak klawiatury, ekranu i myszy.  
  
 <sup>5</sup> wersji `My.Computer`. Zawiera podstawowe informacje o komputerze, takie jak nazwa, dostęp do zegara i tak dalej.  
  
 <sup>6</sup> wersji systemu Windows `My.User`. Ten obiekt jest skojarzony z tożsamością bieżącego wątku.  
  
 <sup>7</sup> wersji web `My.User`. Ten obiekt jest skojarzony z tożsamością użytkownika aplikacji bieżącego żądania HTTP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
