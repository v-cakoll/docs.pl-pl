---
title: My.WebServices — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 9519638c7609b9b1d0f5e07397c46975e2696c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604695"
---
# <a name="mywebservices-object"></a>My.WebServices — Obiekt
Udostępnia właściwości umożliwiające tworzenie i uzyskiwanie dostępu do jednego wystąpienia każdej usługi XML sieci Web odwołuje się do bieżącego projektu.  
  
## <a name="remarks"></a>Uwagi  
 `My.WebServices` Obiektu zawiera wystąpienie poszczególnych usług sieci Web odwołuje się do bieżącego projektu. Każde wystąpienie jest tworzone na żądanie. Dostęp do tych usług sieci Web za pośrednictwem właściwości `My.WebServices` obiektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, który uzyskuje dostęp do właściwości. Każda klasa, która dziedziczy <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> to usługa sieci Web. Informacje dotyczące dodawania usługi sieci Web do projektu, zobacz [podczas uzyskiwania dostępu do usługi sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Obiekt udostępnia tylko usługi sieci Web skojarzony z bieżącego projektu. Nie ma dostępu do usług sieci Web zadeklarowany w przywoływane biblioteki dll. Aby uzyskać dostęp do usługi sieci Web, która udostępnia bibliotekę DLL, należy użyć kwalifikowaną nazwę usługi sieci Web w postaci *DllName*. *WebServiceName*. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do usługi sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt i jego właściwości nie są dostępne dla aplikacji sieci Web.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.WebServices` obiektu zapewnia dostęp do wystąpienia usługi sieci Web odwołuje się do bieżącego projektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, który uzyskuje dostęp do właściwości, a typ właściwości jest taki sam jak typ usługi sieci Web.  
  
> [!NOTE]
>  W przypadku kolizję nazw, nazwa właściwości do uzyskiwania dostępu do usługi sieci Web jest *RootNamespace*_*Namespace*\_*ServiceName*. Rozważmy na przykład dwie usługi sieci Web o nazwie `Service1`. Jeśli jeden z tych usług znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1`, aby dostęp do tej usługi przy użyciu `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Gdy użytkownik najpierw uzyskanie dostępu do `My.WebServices` właściwości obiektu tworzy nowe wystąpienie usługi sieci Web i zapisze go. Kolejne uzyskuje dostęp do tej właściwości zwrócił tego wystąpienia usługi sieci Web.  
  
 Można usunąć usługi sieci Web, przypisując `Nothing` do właściwości tej usługi sieci Web. Metoda ustawiająca właściwości przypisuje `Nothing` przechowywanej wartości. Po przypisaniu wartości inne niż `Nothing` do właściwości metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.  
  
 Można sprawdzić, czy właściwość `My.WebServices` obiekt przechowuje wystąpienie usługi sieci Web przy użyciu `Is` lub `IsNot` operatora. Te operatory można użyć do sprawdzenia, czy wartość właściwości jest `Nothing`.  
  
> [!NOTE]
>  Zazwyczaj `Is` lub `IsNot` operator ma odczytać wartości właściwości do porównania. Jednak jeśli właściwość obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie usługi sieci Web, a następnie zwraca tego wystąpienia. Jednak kompilator Visual Basic traktuje właściwości `My.WebServices` specjalnie obiektów i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmiany jego wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wywołuje `FahrenheitToCelsius` metody `TemperatureConverter` usługi XML sieci Web i zwraca wynik.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Na przykład do pracy projektu musi odwoływać się usługi sieci Web o nazwie `Converter`, i czy usługa sieci Web musi ujawniać `ConvertTemperature` metody. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do usługi sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Ten kod nie działa w projekcie aplikacji sieci Web.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Typ projektu|Dostępne|  
|---|---|  
|Aplikacja systemu Windows|**Tak**|  
|Biblioteka klas|**Tak**|  
|Aplikacja konsoli|**Tak**|  
|Biblioteka formantów systemu Windows|**Tak**|  
|Biblioteka formantów sieci Web|**Tak**|  
|Usługa systemu Windows|**Tak**|  
|Witryna sieci Web|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
