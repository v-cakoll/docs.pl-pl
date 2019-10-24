---
title: Jak My zależy od typu projektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 989329da7dc57cd50b9ce6c88117152d0cb93d66
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775198"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Jak My zależy od typu projektu (Visual Basic)
`My` uwidacznia tylko te obiekty, które są wymagane przez określony typ projektu. Na przykład obiekt `My.Forms` jest dostępny w aplikacji Windows Forms, ale nie jest dostępny w aplikacji konsolowej. W tym temacie opisano, które obiekty `My` są dostępne w różnych typach projektów.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Moje w aplikacjach i witrynach sieci Web systemu Windows  
 `My` uwidacznia tylko obiekty, które są przydatne w bieżącym typie projektu; pomija obiekty, które nie są stosowane. Na przykład na poniższej ilustracji przedstawiono `My` model obiektów w Windows Forms projekcie.  
  
 ![Diagram pokazujący model my Object w aplikacji Windows Forms.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 W projekcie witryny sieci Web `My` uwidacznia obiekty, które są istotne dla deweloperów sieci Web (takich jak obiekty `My.Request` i `My.Response`) przy jednoczesnym pomijaniu obiektów, które nie są istotne (takie jak obiekt `My.Forms`). Na poniższej ilustracji przedstawiono model obiektów `My` w projekcie witryny sieci Web:  
  
 ![Diagram przedstawiający mój model obiektów w aplikacji sieci Web.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Szczegóły projektu  
 W poniższej tabeli przedstawiono, które obiekty `My` są domyślnie włączone dla ośmiu typów projektów: aplikacji systemu Windows, biblioteki klas, aplikacji konsolowej, biblioteki formantów systemu Windows, biblioteki formantów sieci Web, usługi systemu Windows, pustej i witryny sieci Web.  
  
 Istnieją trzy wersje obiektu `My.Application`, dwie wersje obiektu `My.Computer` i dwie wersje obiektu `My.User`. Szczegóły dotyczące tych wersji są podane w przypisach po tabeli.  
  
|Mój obiekt|Aplikacja systemu Windows|Biblioteka klas|Aplikacja konsoli|Biblioteka formantów systemu Windows|Biblioteka formantów sieci Web|Usługa systemu Windows|Pusty|Witryna sieci Web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Tak** <sup>1</sup>|**Tak** <sup>2</sup>|**Tak** <sup>3</sup>|**Tak** <sup>2</sup>|Nie|**Tak** <sup>3</sup>|Nie|Nie|  
|`My.Computer`|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>4</sup>|**Tak** <sup>5</sup>|**Tak** <sup>4</sup>|Nie|**Tak** <sup>5</sup>|  
|`My.Forms`|**Opcję**|Nie|Nie|**Opcję**|Nie|Nie|Nie|Nie|  
|`My.Log`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Opcję**|  
|`My.Request`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Opcję**|  
|`My.Resources`|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|Nie|Nie|  
|`My.Response`|Nie|Nie|Nie|Nie|Nie|Nie|Nie|**Opcję**|  
|`My.Settings`|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|Nie|Nie|  
|`My.User`|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>6</sup>|**Tak** <sup>7</sup>|**Tak** <sup>6</sup>|Nie|**Tak** <sup>7</sup>|  
|`My.WebServices`|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|**Opcję**|Nie|Nie|  
  
 <sup>1</sup> Windows Forms wersja `My.Application`. Pochodzi z wersji konsoli (patrz adnotacja 3); dodaje obsługę współpracy z oknami aplikacji i udostępnia model aplikacji Visual Basic.  
  
 <sup>2</sup> wersja biblioteki `My.Application`. Zapewnia podstawowe funkcje, które są konieczne przez aplikację: umożliwia członkom zapisywanie w dzienniku aplikacji i uzyskiwanie dostępu do informacji o aplikacji.  
  
 <sup>3</sup> wersja konsoli `My.Application`. Pochodzi z wersji biblioteki (patrz adnotacja 2) i dodaje dodatkowych członków do uzyskiwania dostępu do argumentów wiersza polecenia i informacji o wdrożeniu technologii ClickOnce.  
  
 <sup>4</sup> wersja `My.Computer` systemu Windows. Pochodzi z wersji serwera (patrz adnotacja 5) i zapewnia dostęp do przydatnych obiektów na komputerze klienckim, takich jak klawiatura, ekran i mysz.  
  
 <sup>5</sup> wersja serwera `My.Computer`. Zawiera podstawowe informacje o komputerze, takie jak nazwa, dostęp do zegara i tak dalej.  
  
 <sup>6</sup> wersja `My.User` systemu Windows. Ten obiekt jest skojarzony z bieżącą tożsamością wątku.  
  
 <sup>7</sup> wersja sieci Web `My.User`. Ten obiekt jest skojarzony z tożsamością użytkownika bieżącego żądania HTTP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-Definiuj (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)
- [My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
