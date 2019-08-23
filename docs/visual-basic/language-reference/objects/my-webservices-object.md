---
title: My. WebServices — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918177"
---
# <a name="mywebservices-object"></a>My.WebServices — Obiekt
Zawiera właściwości służące do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia każdej usługi sieci Web XML, do której odwołuje się bieżący projekt.  
  
## <a name="remarks"></a>Uwagi  
 `My.WebServices` Obiekt zawiera wystąpienie każdej usługi sieci Web, do której odwołuje się bieżący projekt. Każde wystąpienie jest tworzone na żądanie. Dostęp do tych usług sieci Web można uzyskać za pomocą właściwości `My.WebServices` obiektu. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość. Każda klasa, która dziedziczy <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> z, jest usługą sieci Web. Aby uzyskać informacje na temat dodawania usług sieci Web do projektu, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Obiekt uwidacznia tylko usługi sieci Web skojarzone z bieżącym projektem. Nie zapewnia dostępu do usług sieci Web zadeklarowanych w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do usługi sieci Web udostępnianej przez bibliotekę DLL, należy użyć kwalifikowanej nazwy usługi sieci Web w formularzu *nazwa_pliku_dll*.WebServiceName. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt i jego właściwości nie są dostępne dla aplikacji sieci Web.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość `My.WebServices` obiektu zapewnia dostęp do wystąpienia usługi sieci Web, do której odwołuje się bieżący projekt. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość, a typ właściwości jest taka sama jak typ usługi sieci Web.  
  
> [!NOTE]
> W przypadku kolizji nazw nazwa właściwości służącej do uzyskiwania dostępu do usługi sieci Web to *RootNamespace*_*przestrzeń nazw*\_*ServiceName*. Rozważmy na przykład dwie usługi sieci Web `Service1`o nazwie. Jeśli jedna z tych usług znajduje się w głównej przestrzeni `WindowsApplication1` nazw i w przestrzeni `Namespace1`nazw, można uzyskać dostęp do tej usługi `My.WebServices.WindowsApplication1_Namespace1_Service1`za pomocą programu.  
  
 Gdy po raz pierwszy uzyskujesz dostęp `My.WebServices` do jednej z właściwości obiektu, tworzy nowe wystąpienie usługi sieci Web i zapisuje je. Kolejne dostęp do tej właściwości zwracają to wystąpienie usługi sieci Web.  
  
 Usługę sieci Web można usunąć, przypisując `Nothing` do właściwości tej usługi sieci Web. Metoda ustawiająca Właściwość `Nothing` przypisuje do przechowywanej wartości. Jeśli przypiszesz dowolną wartość inną `Nothing` niż właściwość, Metoda ustawiająca <xref:System.ArgumentException> zgłosi wyjątek.  
  
 Można sprawdzić, czy właściwość `My.WebServices` obiektu przechowuje wystąpienie usługi sieci Web za `Is` pomocą operatora or `IsNot` . Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing`.  
  
> [!NOTE]
> Zazwyczaj operator `IsNot` or musi odczytywać wartość właściwości w celu przeprowadzenia porównania. `Is` Jeśli jednak właściwość jest obecnie przechowywana `Nothing`, Właściwość tworzy nowe wystąpienie usługi sieci Web, a następnie zwraca to wystąpienie. Jednak kompilator Visual Basic traktuje właściwości `My.WebServices` obiektu specjalnie i `Is` umożliwia operatorowi or `IsNot` sprawdzenie stanu właściwości bez zmiany jego wartości.  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje `FahrenheitToCelsius` metodę `TemperatureConverter` usługi sieci Web XML i zwraca wynik.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Aby ten przykład działał, projekt musi odwoływać się do usługi sieci Web `Converter`o nazwie, a usługa sieci Web musi `ConvertTemperature` uwidocznić metodę. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
