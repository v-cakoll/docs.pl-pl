---
title: My.WebServices — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 7ae99bec5797591e53c6c77f5d9f88589352104c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862399"
---
# <a name="mywebservices-object"></a>My.WebServices — Obiekt
Udostępnia właściwości do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia poszczególnych usług sieci Web XML odwołuje się do bieżącego projektu.  
  
## <a name="remarks"></a>Uwagi  
 `My.WebServices` Obiekt zawiera wystąpienie każdą usługę sieci Web, które odwołuje się do bieżącego projektu. Każde wystąpienie jest tworzone na żądanie. Dostęp do usługi sieci Web za pomocą właściwości `My.WebServices` obiektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, który uzyskuje dostęp do właściwości. Każda klasa, która dziedziczy z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> to usługa sieci Web. Aby dowiedzieć się, jak dodawanie usług sieci Web do projektu, zobacz [uzyskiwania dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Obiekt udostępnia tylko usługi sieci Web, które są skojarzone z bieżącego projektu. Zapewnia ona dostęp do usług sieci Web, zadeklarowany w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do usługi sieci Web, który zawiera biblioteki DLL, należy użyć kwalifikowaną nazwę usługi sieci Web w postaci *Nazwa_pliku_dll*. *WebServiceName*. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt i jego właściwości nie są dostępne dla aplikacji sieci Web.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.WebServices` obiekt umożliwia dostęp do wystąpienia usługi sieci Web, odwołuje się do bieżącego projektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, który uzyskuje dostęp do właściwości, a typ właściwości jest taka sama jak typ usługi sieci Web.  
  
> [!NOTE]
>  W przypadku kolizji nazw, nazwa właściwości do uzyskiwania dostępu do usługi sieci Web jest *RootNamespace*_*Namespace*\_*ServiceName*. Na przykład, należy wziąć pod uwagę dwie usługi sieci Web o nazwie `Service1`. Jeśli jeden z tych usług jest w głównej przestrzeni nazw `WindowsApplication1` w przestrzeni nazw `Namespace1`, uzyskujesz dostęp do tej usługi przy użyciu `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Po pierwszym uzyskaniu dostępu jednego z `My.WebServices` właściwości obiektu, jego tworzy nowe wystąpienie usługi sieci Web i zapisuje go. Kolejne uzyskuje dostęp do właściwości zwracają to wystąpienie usługi sieci Web.  
  
 Dispose na usługi sieci Web, przypisując `Nothing` do właściwości tej usługi sieci Web. Metoda ustawiająca właściwości przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolnej wartości innych niż `Nothing` dla właściwości, metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.  
  
 Możesz sprawdzić, czy właściwość `My.WebServices` obiekt przechowuje wystąpienie usługi sieci Web za pomocą `Is` lub `IsNot` operatora. Aby sprawdzić, czy wartość właściwości można używać tych operatorów `Nothing`.  
  
> [!NOTE]
>  Zazwyczaj `Is` lub `IsNot` operator ma zostać odczytana wartość właściwości, które ma wykonać porównanie. Jednakże jeśli właściwość jest obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie usługi sieci Web, a następnie zwraca tego wystąpienia. Jednak kompilator języka Visual Basic traktuje właściwości `My.WebServices` specjalnie obiektu i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmieniania jego wartości.  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje `FahrenheitToCelsius` metody `TemperatureConverter` usługi sieci Web XML i zwraca wynik.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 W tym przykładzie do pracy projektu musi odwoływać się do usługi sieci Web o nazwie `Converter`, i musi uwidaczniać tej usługi sieci Web `ConvertTemperature` metody. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Ten kod nie działa w projekcie aplikacji sieci Web.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Typ projektu|Dostępne|  
|---|---|  
|Aplikacja Windows|**Tak**|  
|Biblioteka klas|**Tak**|  
|Aplikacja konsoli|**Tak**|  
|Biblioteka formantów Windows|**Tak**|  
|Biblioteka formantów sieci Web|**Tak**|  
|Usługa systemu Windows|**Tak**|  
|Witryna sieci Web|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
