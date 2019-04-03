---
title: Jak My zależy od typu projektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 743160889c4f24a9edb2d0f9799662a74c5061fb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842086"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Jak My zależy od typu projektu (Visual Basic)
`My` udostępnia tylko te obiekty, które są wymagane przez określonego typu projektu. Na przykład `My.Forms` obiekt jest dostępny w aplikacji Windows Forms, ale nie jest dostępna w aplikacji konsoli. W tym temacie opisano, które `My` obiekty są dostępne w różnych typach projektów.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Moje Windows w aplikacji i witryn sieci Web  
 `My` udostępnia tylko te obiekty, które są przydatne do bieżącego typu projektu. Pomija go obiekty, które nie mają zastosowania. Na przykład na poniższej ilustracji przedstawiono `My` model obiektu w projekcie programu Windows Forms.  
  
 ![Kształt Moje w aplikacji Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 W projekcie witryny sieci Web `My` udostępnia obiekty, które są istotne dla deweloperów sieci Web (takie jak `My.Request` i `My.Response` obiektów) podczas pomijanie obiektów, które nie są istotne (takie jak `My.Forms` obiektu). Na poniższej ilustracji przedstawiono `My` model obiektu projektu witryny sieci Web:  
  
 ![Kształt Moje w aplikacji sieci Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Szczegóły projektu  
 W poniższej tabeli przedstawiono, które `My` obiekty są domyślnie włączone dla osiem typów projektów: Windows aplikacji, klasy biblioteki, aplikacji konsoli, Windows Biblioteka kontrolek, sieci Web Biblioteka kontrolek, Windows usługi, pusta i witryny sieci Web.  
  
 Istnieją trzy wersje `My.Application` object, dwie wersje `My.Computer` obiektu i dwie wersje `My.User` obiektu szczegółowe informacje o tych wersjach są podane w przypisy pod tabelą.  
  
|Mój obiekt|Aplikacja Windows|Biblioteka klas|Aplikacja konsoli|Biblioteka formantów Windows|Biblioteka formantów sieci Web|Usługa systemu Windows|Pusty|Witryna sieci Web|  
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
  
 <sup>1</sup> wersję Windows Forms `My.Application`. Wersja konsoli jest pochodną (patrz Uwaga 3); dodaje obsługę interakcji z aplikacji systemu windows i udostępnia model aplikacji Visual Basic.  
  
 <sup>2</sup> wersję biblioteki `My.Application`. Oferuje podstawowe funkcje wymagane przez aplikację: oferuje elementy członkowskie do zapisu w dzienniku aplikacji i uzyskiwanie dostępu do informacji o aplikacji.  
  
 <sup>3</sup> wersji konsoli `My.Application`. Pochodzi z wersji biblioteki (patrz Uwaga 2), a dodatkowe elementy członkowskie są dodawane do uzyskiwania dostępu do argumentów wiersza polecenia aplikacji oraz informacje dotyczące wdrażania ClickOnce.  
  
 <sup>4</sup> wersję Windows `My.Computer`. Wersja serwera jest pochodną (patrz Uwaga 5) i zapewnia dostęp do przydatnych obiektów na komputerze klienckim, na przykład klawiatury, ekranu i myszy.  
  
 <sup>5</sup> wersję serwera `My.Computer`. Zawiera podstawowe informacje o komputerze, takie jak nazwa, dostęp do zegara i tak dalej.  
  
 <sup>6</sup> wersję Windows `My.User`. Ten obiekt jest skojarzony z bieżącą tożsamość wątku.  
  
 <sup>7</sup> wersji internetowej procesu `My.User`. Ten obiekt jest skojarzone z tożsamością użytkownika aplikacji bieżącego żądania HTTP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
