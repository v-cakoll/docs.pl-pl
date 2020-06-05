---
title: My.WebServices — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a52f9f5f5b044273a45da5ef9478e2212def57a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372365"
---
# <a name="mywebservices-object"></a>My.WebServices — Obiekt
Zawiera właściwości służące do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia każdej usługi sieci Web XML, do której odwołuje się bieżący projekt.  
  
## <a name="remarks"></a>Uwagi  
 `My.WebServices`Obiekt zawiera wystąpienie każdej usługi sieci Web, do której odwołuje się bieżący projekt. Każde wystąpienie jest tworzone na żądanie. Dostęp do tych usług sieci Web można uzyskać za pomocą właściwości `My.WebServices` obiektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość. Każda klasa, która dziedziczy z, <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> jest usługą sieci Web. Aby uzyskać informacje na temat dodawania usług sieci Web do projektu, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices`Obiekt uwidacznia tylko usługi sieci Web skojarzone z bieżącym projektem. Nie zapewnia dostępu do usług sieci Web zadeklarowanych w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do usługi sieci Web udostępnianej przez bibliotekę DLL, należy użyć kwalifikowanej nazwy usługi sieci Web w formularzu *nazwa_pliku_dll*. *WebServiceName*. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt i jego właściwości nie są dostępne dla aplikacji sieci Web.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.WebServices` obiektu zapewnia dostęp do wystąpienia usługi sieci Web, do której odwołuje się bieżący projekt. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość, a typ właściwości jest taka sama jak typ usługi sieci Web.  
  
> [!NOTE]
> W przypadku kolizji nazw nazwa właściwości służącej do uzyskiwania dostępu do usługi sieci Web to *RootNamespace*_*przestrzeń nazw* \_ *ServiceName*. Rozważmy na przykład dwie usługi sieci Web o nazwie `Service1` . Jeśli jedna z tych usług znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1` , można uzyskać dostęp do tej usługi za pomocą programu `My.WebServices.WindowsApplication1_Namespace1_Service1` .  
  
 Gdy po raz pierwszy uzyskujesz dostęp do jednej z `My.WebServices` właściwości obiektu, tworzy nowe wystąpienie usługi sieci Web i zapisuje je. Kolejne dostęp do tej właściwości zwracają to wystąpienie usługi sieci Web.  
  
 Usługę sieci Web można usunąć, przypisując `Nothing` do właściwości tej usługi sieci Web. Metoda ustawiająca Właściwość przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolną wartość inną niż `Nothing` Właściwość, Metoda ustawiająca zgłosi <xref:System.ArgumentException> wyjątek.  
  
 Można sprawdzić, czy właściwość `My.WebServices` obiektu przechowuje wystąpienie usługi sieci Web za pomocą `Is` `IsNot` operatora OR. Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing` .  
  
> [!NOTE]
> Zazwyczaj `Is` `IsNot` operator or musi odczytywać wartość właściwości w celu przeprowadzenia porównania. Jeśli jednak właściwość jest obecnie przechowywana `Nothing` , Właściwość tworzy nowe wystąpienie usługi sieci Web, a następnie zwraca to wystąpienie. Jednak kompilator Visual Basic traktuje właściwości `My.WebServices` obiektu specjalnie i umożliwia `Is` `IsNot` operatorowi or sprawdzenie stanu właściwości bez zmiany jego wartości.  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje `FahrenheitToCelsius` metodę `TemperatureConverter` usługi sieci Web XML i zwraca wynik.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Aby ten przykład działał, projekt musi odwoływać się do usługi sieci Web o nazwie `Converter` , a usługa sieci Web musi uwidocznić `ConvertTemperature` metodę. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../developing-apps/programming/accessing-application-web-services.md).  
  
 Ten kod nie działa w projekcie aplikacji sieci Web.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Project type (Typ projektu)|Dostępne|  
|---|---|  
|Aplikacja systemu Windows|**Tak**|  
|Biblioteka klas|**Tak**|  
|Aplikacja konsoli|**Tak**|  
|Biblioteka formantów systemu Windows|**Tak**|  
|Biblioteka formantów sieci Web|**Tak**|  
|Usługa systemu Windows|**Tak**|  
|Witryna sieci Web|Nie|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uzyskiwanie dostępu do usług internetowych aplikacji](../../developing-apps/programming/accessing-application-web-services.md)
