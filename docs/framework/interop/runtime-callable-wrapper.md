---
title: "Wywoływana otoka środowiska uruchomieniowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 980ed0a10c4e8152da20846710b21c244a341271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-callable-wrapper"></a>Wywoływana otoka środowiska uruchomieniowego
Środowisko uruchomieniowe języka wspólnego przedstawia obiekty COM za pośrednictwem serwera proxy, nazywany wywoływana otoka środowiska uruchomieniowego (otoki RCW). Mimo że otoki RCW wydaje się być obiekt zwykłej do klientów platformy .NET, jego podstawową funkcją jest do organizowania wywołań między klientem .NET obiektu COM.  
  
 Środowisko uruchomieniowe tworzy dokładnie jeden otoki RCW dla każdego obiektu modelu COM, niezależnie od liczby odwołań, które istnieją w tym obiekcie. Środowisko uruchomieniowe obsługuje pojedynczy otoki RCW na proces dla każdego obiektu.  Jeśli tworzenie otoki RCW w jednej domenie aplikacji lub typu apartment, a następnie przekazać odwołanie do innej domeny aplikacji lub typu apartment, będzie używany serwer proxy, aby pierwszy obiekt.  Jak pokazano na poniższej ilustracji, dowolną liczbę zarządzanych klientów może zawierać odwołania do obiektów COM, które udostępniają INew i INewer interfejsów.  
  
 ![Otoka RCW](../../../docs/framework/interop/media/rcw.gif "otoki rcw")  
Uzyskiwanie dostępu do obiektów COM za pomocą wywoływana otoka środowiska uruchomieniowego  
  
 Przy użyciu metadanych pochodzące z biblioteki typów, środowisko uruchomieniowe tworzy obiekt COM, wywoływana i otoki dla tego obiektu. Każdy otoki RCW obsługuje pamięć podręczną wskaźniki interfejsu w obiekcie COM zawijany i zwalnia jego odwołania do obiektu COM otoki RCW jest już potrzebne. Środowisko uruchomieniowe przeprowadzają otoki RCW wyrzucanie elementów bezużytecznych.  
  
 Wśród innych działań otoki RCW marshals danych między zarządzanymi i niezarządzanymi kodu w imieniu opakowana obiektu. W szczególności otoki RCW umożliwia organizowanie metody argumentów i wartości zwracanych metody zawsze, gdy klient i serwer mają różne reprezentacje danych przesyłanych między nimi.  
  
 Standardowa otoki wymusza wbudowane reguły kierowania. Na przykład gdy klienta .NET przekazuje typu ciąg jako część argumentu do niezarządzanego obiektu, otoka konwertuje ciąg na typ BSTR. Obiekt wywołujący obiektu COM należy przywrócić BSTR zarządzanych wywołującego, otrzymuje ciąg. Zarówno klient, jak i serwer wysyłania i odbierania danych, które są znane do nich. Inne typy wymagają brak konwersji. Na przykład standardowe otoki zawsze przekazuje 4-bajtowych liczb całkowitych między zarządzanymi i niezarządzanymi kodu bez konwersji typu.  
  
## <a name="marshaling-selected-interfaces"></a>Przekazywanie wybranego interfejsów  
 Podstawowym celem [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW) jest ukrycie różnice między zarządzanymi i niezarządzanymi modele programowania. Aby utworzyć płynne przejście, otoki RCW zużywa wybrane interfejsy COM bez narażania ich do klienta .NET, jak pokazano na poniższej ilustracji.  
  
 ![Otoka RCW z interfejsów](../../../docs/framework/interop/media/rcwwithinterfaces.gif "rcwwithinterfaces")  
Interfejsy modelu COM i wywoływana otoka środowiska uruchomieniowego  
  
 Po utworzeniu jako obiekt z wczesnym wiązaniem otoki RCW jest określonego typu. Implementuje interfejsy implementuje i udostępnia metody, właściwości i zdarzeń z interfejsów obiektu obiektu COM. Na ilustracji uwidacznia interfejs INew otoki RCW, ale zużywa **IUnknown** i **IDispatch** interfejsów. Ponadto otoki RCW przedstawia wszystkie elementy członkowskie interfejsu INew do klienta programu .NET.  
  
 Otoka RCW korzysta z interfejsów wymienionych w poniższej tabeli, które są udostępniane przez obiektu, do którego jest zawijany.  
  
|Interface|Opis|  
|---------------|-----------------|  
|**IDispatch**|Późne powiązania do obiektów COM za pomocą odbicia.|  
|**IErrorInfo**|Dostarcza opis tekstowy błąd, źródła pliku pomocy, kontekst pomocy i identyfikator GUID interfejsu, który zdefiniowano błędu (zawsze **GUID_NULL** dla klas .NET).|  
|**IProvideClassInfo**|Jeśli trwa obiektu COM opakowana implementuje **IProvideClassInfo**, otoki RCW wyodrębnia informacje o typie w tym interfejsie, aby zapewnić lepsze typu tożsamości.|  
|**IUnknown**|Tożsamość obiektu, koercja typu i zarządzanie okresem istnienia:<br /><br /> — Identity obiekt<br />     Środowisko uruchomieniowe rozróżnia obiektów COM, porównując wartości **IUnknown** interfejsu dla każdego obiektu.<br />— Koercja typ<br />     Otoka RCW rozpoznaje odnajdywania typu dynamicznego wykonywane przez **QueryInterface** metody.<br />-Zarządzanie okresem istnienia<br />     Przy użyciu **QueryInterface** metoda pobiera otoki RCW i zawiera odwołanie do niezarządzanego obiektu, dopóki środowisko uruchomieniowe przeprowadzają otoki, które zwalnia niezarządzane obiekt wyrzucanie elementów bezużytecznych.|  
  
 Otoka RCW zużywa opcjonalnie interfejsów wymienionych w poniższej tabeli, które są udostępniane przez obiektu, do którego jest zawijany.  
  
|Interface|Opis|  
|---------------|-----------------|  
|**IConnectionPoint** i **IConnectionPointContainer**|Obiektów konwertuje otoki RCW, które udostępniają styl zdarzenie punktu połączenia na podstawie delegata zdarzenia.|  
|**Interfejs IDispatchEx**|Jeśli klasa implementuje **IDispatchEx**, implementuje otoki RCW **IExpando**. **IDispatchEx** interfejsu jest rozszerzeniem **IDispatch** interfejsu, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania i z uwzględnieniem wielkości liter wywoływanie elementów członkowskich.|  
|**Interfejsu IEnumVARIANT**|Umożliwia typów COM, które obsługują wyliczenia powinien być traktowany jako kolekcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Otoki COM](../../../docs/framework/interop/com-wrappers.md)  
 [Przekazywanie wybranego interfejsów](http://msdn.microsoft.com/en-us/fdb97fd0-f694-4832-bf15-a4e7cf413840)  
 [Wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Biblioteki typów na zestaw konwersja — podsumowanie](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
