---
title: Wywoływana otoka środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3abce6ef7cb1d3287d9c8b7ceb9333f209e75ad
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219529"
---
# <a name="runtime-callable-wrapper"></a>Wywoływana otoka środowiska uruchomieniowego
Środowisko uruchomieniowe języka wspólnego udostępnia obiekty COM za pośrednictwem serwera proxy, wywoływana otoka wywoływana w czasie wykonywania (RCW). Mimo że RCW wydaje się być zwykły obiekt do klientów programu .NET, jego podstawową funkcją jest kierowanie wywołań między klientem platformy .NET i obiekt COM.  
  
 Środowisko uruchomieniowe tworzy RCW dokładnie jeden dla każdego obiektu COM, bez względu na liczbę odwołań, które istnieją na tym obiekcie. Środowisko uruchomieniowe przechowuje pojedynczego RCW na proces dla każdego obiektu.  Jeśli tworzenie RCW w jednej domenie aplikacji lub typu apartment, a następnie przekazać odwołanie do innej domeny aplikacji lub typu apartment, będzie używany serwer proxy, aby pierwszy obiekt.  Jak pokazano na poniższej ilustracji, dowolną liczbę zarządzanych klientów może zawierać odwołania do obiektów COM, które uwidaczniają INew i INewer interfejsów.  
  
 ![RCW](./media/rcw.gif "rcw")  
Uzyskiwanie dostępu do obiektów COM za pomocą wywoływana otoka środowiska uruchomieniowego  
  
 Przy użyciu metadanych pochodzące z biblioteki typów, środowisko uruchomieniowe tworzy wywoływanego obiektu COM i otoki dla tego obiektu. Każdy RCW obsługuje pamięć podręczną wskaźniki interfejsu na obiekt COM, otacza i zwalnia swoje odwołanie do obiektu COM, gdy RCW nie jest już potrzebny. Środowisko uruchomieniowe wykonuje wyrzucanie elementów bezużytecznych na RCW.  
  
 Wśród innych działań RCW kieruje dane między kodem zarządzanym i niezarządzanym imieniu opakowana obiektu. W szczególności RCW zapewnia marshaling dla argumentów metody i wartości zwracane metody zawsze wtedy, gdy klient i serwer mają różne reprezentacje danych przesyłanych między nimi.  
  
 Otoki standardowe wymusza wbudowane reguły dotyczące organizowania. Na przykład podczas klienta platformy .NET przekazuje typ ciągu jako część argument do niezarządzanego obiektu, otoka konwertuje ciąg na typ BSTR. Obiekt COM powinna zwrócić BSTR zarządzanego obiektu wywołującego, obiekt wywołujący odbiera ciąg. Klient i serwer wysyłania i odbierania danych, które są znane do nich. Inne typy wymagają bez konwersji. Na przykład standardowy otoki będzie zawsze przekazuj parametr 4-bajtowa liczba całkowita między kodem zarządzanym i niezarządzanym bez konwersji typu.  
  
## <a name="marshaling-selected-interfaces"></a>Organizowanie wybranych interfejsów  
 Podstawowym celem [wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md) (RCW) jest ukrycie różnice między zarządzanymi i niezarządzanymi modelach programowania. Aby utworzyć płynne przejście, RCW zużywa wybranych interfejsów COM bez narażania ich do klienta platformy .NET, jak pokazano na poniższej ilustracji.  
  
 ![RCW przy użyciu interfejsów](./media/rcwwithinterfaces.gif "rcwwithinterfaces")  
Wywoływana otoka środowiska uruchomieniowego i interfejsy modelu COM  
  
 Gdy tworzony jest obiekt z wczesnym wiązaniem, RCW jest określonego typu. Implementuje interfejsy, że obiekt COM implementuje i udostępnia metody, właściwości i zdarzeń z interfejsów obiektów. Na ilustracji, udostępnia interfejs INew RCW, ale zużywa **IUnknown** i **IDispatch** interfejsów. Ponadto RCW uwidacznia wszystkie elementy członkowskie interfejs INew do klienta platformy .NET.  
  
 RCW zużywa interfejsów wymienionych w poniższej tabeli, które są udostępniane przez obiekt, który otacza.  
  
|Interface|Opis|  
|---------------|-----------------|  
|**IDispatch**|Aby uzyskać późne powiązania do obiektów COM w drodze odbicia.|  
|**IErrorInfo**|Zawiera opis tekstowy błędu, źródło, pliku pomocy, Pomoc kontekstowa i identyfikator GUID interfejs który jest zdefiniowany błędu (zawsze **GUID_NULL** dla klas platformy .NET).|  
|**IProvideClassInfo**|Jeśli jest obiektu modelu COM opakowane implementuje **IProvideClassInfo**, RCW wyodrębnia informacje o typie, w tym interfejsie w celu zapewnienia lepszej tożsamości typu.|  
|**IUnknown**|Tożsamość obiektu, przekształcenie typu i zarządzanie okresem istnienia:<br /><br /> — Identity obiekt<br />     Środowisko uruchomieniowe rozróżnia obiekty COM przez porównanie wartości **IUnknown** interfejsu dla każdego obiektu.<br />— Wymuszanie typ<br />     RCW rozpoznaje odnajdywania typu dynamicznego, wykonywane przez **QueryInterface** metody.<br />— Zarządzanie okresem istnienia<br />     Za pomocą **QueryInterface** metody RCW pobiera i zawiera odwołanie do obiektu niezarządzanych, dopóki środowisko uruchomieniowe wykonuje wyrzucanie elementów bezużytecznych na otoki, która uwalnia niezarządzanych obiektów.|  
  
 Opcjonalnie RCW korzysta z interfejsów wymienionych w poniższej tabeli, które są udostępniane przez obiekt, który otacza.  
  
|Interface|Opis|  
|---------------|-----------------|  
|**IConnectionPoint** i **interfejsy IConnectionPointContainer**|Obiekty konwertuje RCW, które uwidaczniają styl zdarzenie punktu połączenia na podstawie delegata zdarzenia.|  
|**IDispatchEx**|Jeśli klasa implementuje **IDispatchEx**, implementuje RCW **IExpando**. **IDispatchEx** interfejs jest rozszerzeniem **IDispatch** interfejs, który, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania oraz wielkość liter wywoływanie elementów członkowskich.|  
|**Interfejs IEnumVARIANT**|Umożliwia typów modelu COM, które obsługują wyliczenia powinien być traktowany jako kolekcji.|  
  
## <a name="see-also"></a>Zobacz także
- [Otoki COM](com-wrappers.md)
- [Wywoływana otoka COM](com-callable-wrapper.md)
- [Biblioteki typów na zestaw konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
