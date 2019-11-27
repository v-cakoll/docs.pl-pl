---
title: My.WebServices — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 290d025985663bc45fe605a2e9904fc90fb2bc63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350337"
---
# <a name="mywebservices-object"></a>My.WebServices — Obiekt
Zawiera właściwości służące do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia każdej usługi sieci Web XML, do której odwołuje się bieżący projekt.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.WebServices` zapewnia wystąpienie każdej usługi sieci Web, do której odwołuje się bieżący projekt. Każde wystąpienie jest tworzone na żądanie. Dostęp do tych usług sieci Web można uzyskać za pomocą właściwości obiektu `My.WebServices`. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość. Każda klasa, która dziedziczy po <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>, jest usługą sieci Web. Aby uzyskać informacje na temat dodawania usług sieci Web do projektu, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt `My.WebServices` uwidacznia tylko usługi sieci Web skojarzone z bieżącym projektem. Nie zapewnia dostępu do usług sieci Web zadeklarowanych w przywoływanych bibliotekach DLL. Aby uzyskać dostęp do usługi sieci Web udostępnianej przez bibliotekę DLL, należy użyć kwalifikowanej nazwy usługi sieci Web w formularzu *nazwa_pliku_dll*. *WebServiceName*. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Obiekt i jego właściwości nie są dostępne dla aplikacji sieci Web.  
  
## <a name="properties"></a>Właściwości  
 Każda właściwość obiektu `My.WebServices` zapewnia dostęp do wystąpienia usługi sieci Web, do której odwołuje się bieżący projekt. Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość, a typ właściwości jest taka sama jak typ usługi sieci Web.  
  
> [!NOTE]
> W przypadku kolizji nazw nazwa właściwości do uzyskiwania dostępu do usługi sieci Web to *RootNamespace*_*przestrzeń nazw*\_*ServiceName*. Rozważmy na przykład dwie usługi sieci Web o nazwie `Service1`. Jeśli jedna z tych usług znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w `Namespace1`przestrzeni nazw, można uzyskać dostęp do tej usługi przy użyciu `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Gdy po raz pierwszy uzyskujesz dostęp do jednej z właściwości obiektu `My.WebServices`, tworzy nowe wystąpienie usługi sieci Web i zapisuje je. Kolejne dostęp do tej właściwości zwracają to wystąpienie usługi sieci Web.  
  
 Usługę sieci Web można usunąć, przypisując `Nothing` do właściwości tej usługi sieci Web. Metoda ustawiająca Właściwość przypisuje `Nothing` do przechowywanej wartości. Jeśli przypiszesz dowolną wartość inną niż `Nothing` do właściwości, Metoda ustawiająca zgłosi wyjątek <xref:System.ArgumentException>.  
  
 Możesz sprawdzić, czy właściwość obiektu `My.WebServices` przechowuje wystąpienie usługi sieci Web za pomocą operatora `Is` lub `IsNot`. Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing`.  
  
> [!NOTE]
> Zazwyczaj operator `Is` lub `IsNot` musi odczytywać wartość właściwości w celu przeprowadzenia porównania. Jeśli jednak Właściwość aktualnie przechowuje `Nothing`, Właściwość tworzy nowe wystąpienie usługi sieci Web, a następnie zwraca to wystąpienie. Jednak kompilator Visual Basic traktuje właściwości obiektu `My.WebServices` specjalnie i umożliwia operatorowi `Is` lub `IsNot` sprawdzenie stanu właściwości bez zmiany jej wartości.  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje metodę `FahrenheitToCelsius` usługi sieci Web `TemperatureConverter` XML i zwraca wynik.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Aby ten przykład działał, projekt musi odwoływać się do usługi sieci Web o nazwie `Converter`, a usługa sieci Web musi uwidocznić metodę `ConvertTemperature`. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Ten kod nie działa w projekcie aplikacji sieci Web.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="availability-by-project-type"></a>Dostępność według typu projektu  
  
|Typ projektu|Dostępne|  
|---|---|  
|Aplikacja systemu Windows|**Opcję**|  
|Biblioteka klas|**Opcję**|  
|Aplikacja konsoli|**Opcję**|  
|Biblioteka formantów systemu Windows|**Opcję**|  
|Biblioteka formantów sieci Web|**Opcję**|  
|Usługa systemu Windows|**Opcję**|  
|Witryna sieci Web|Nie|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
