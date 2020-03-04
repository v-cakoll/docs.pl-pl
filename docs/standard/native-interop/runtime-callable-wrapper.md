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
ms.openlocfilehash: 0b448379fba965060fdf3bf067e65374f40d1fc2
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156013"
---
# <a name="runtime-callable-wrapper"></a>Wywoływana otoka środowiska uruchomieniowego
Środowisko uruchomieniowe języka wspólnego udostępnia obiekty COM za pomocą serwera proxy zwanego otoką (otoka) środowiska uruchomieniowego. Chociaż Otoka RCW wydaje się być zwykłym obiektem dla klientów platformy .NET, jej podstawową funkcją jest kierowanie wywołań między klientem .NET a obiektem COM.  
  
 Środowisko uruchomieniowe tworzy dokładnie jedną otokę RCW dla każdego obiektu COM, niezależnie od liczby odwołań istniejących w tym obiekcie. Środowisko uruchomieniowe utrzymuje pojedynczą OTOKę na każdy proces dla każdego obiektu.  Jeśli utworzysz otokę RCW w jednej domenie lub apartamentu aplikacji, a następnie przekażesz odwołanie do innej domeny lub apartamentu aplikacji, zostanie użyty serwer proxy do pierwszego obiektu.  Jak widać na poniższej ilustracji, każda liczba zarządzanych klientów może przechowywać odwołanie do obiektów COM, które uwidaczniają interfejsy INew i INewer.  

Na poniższej ilustracji przedstawiono proces uzyskiwania dostępu do obiektów COM za pomocą otoki możliwej do uruchomienia:

 ![Proces uzyskiwania dostępu do obiektów COM za pomocą OTOKi.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 Przy użyciu metadanych pochodzących z biblioteki typów środowisko uruchomieniowe tworzy zarówno wywoływany obiekt COM, jak i otokę dla tego obiektu. Każda pozostała OTOKa utrzymuje pamięć podręczną wskaźników interfejsu w obiekcie COM, która otacza i zwalnia odwołanie do obiektu COM, gdy Otoka RCW nie jest już wymagana. Środowisko uruchomieniowe wykonuje wyrzucanie elementów bezużytecznych dla otoki RCW.  
  
 W przypadku innych działań Otoka RCW udostępnia dane między zarządzanym i niezarządzanym kodem w imieniu opakowanego obiektu. Otoka RCW zapewnia kierowanie argumentów metod i zwracanych wartości metod za każdym razem, gdy klient i serwer mają różne reprezentacje danych przekazywanych między nimi.  
  
 Otoka standardowa wymusza wbudowane reguły organizowania. Na przykład gdy klient platformy .NET przekazuje typ ciągu jako część argumentu do niezarządzanego obiektu, otoka konwertuje ciąg na typ BSTR. Jeśli obiekt COM zwraca element BSTR do zarządzanego obiektu wywołującego, obiekt wywołujący otrzymuje ciąg. Zarówno klient, jak i serwer wysyłają i odbierają dane, które są dla nich znane. Inne typy nie wymagają konwersji. Na przykład, otoka standardowa zawsze przekaże 4-bajtową liczbę całkowitą między zarządzanym i niezarządzanym kodem bez konwertowania typu.  
  
## <a name="marshaling-selected-interfaces"></a>Kierowanie wybranych interfejsów  
 Głównym celem [otoki wywoływanej środowiska uruchomieniowego](runtime-callable-wrapper.md) (RCW) jest ukrywanie różnic między zarządzanymi i niezarządzanymi modelami programowania. W celu zapewnienia bezproblemowego przejścia Otoka RCW wykorzystuje wybrane interfejsy COM bez udostępniania ich klientom platformy .NET, jak pokazano na poniższej ilustracji.

 Na poniższej ilustracji przedstawiono interfejsy COM i otokę, która umożliwia wywoływanie środowiska uruchomieniowego:
  
 ![Zrzut ekranu przedstawiający otokę w środowisku uruchomieniowym z interfejsami.](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 Podczas tworzenia jako obiekt z wczesnym wiązaniem, OTOKa jest określonego typu. Implementuje interfejsy, które obiekt COM implementuje i uwidacznia metody, właściwości i zdarzenia z interfejsów obiektu. Na ilustracji Otoka RCW uwidacznia interfejs INew, ale zużywa interfejsy **IUnknown** i **IDispatch** . Ponadto Otoka RCW uwidacznia wszystkie elementy członkowskie interfejsu INew do klienta platformy .NET.  
  
 Otoka RCW zużywa interfejsy wymienione w poniższej tabeli, które są uwidaczniane przez obiekt, który jest zawijany.  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|**IDispatch**|Dla późnego wiązania do obiektów COM przy użyciu odbicia.|  
|**IErrorInfo**|Zawiera tekstowy opis błędu, jego źródło, plik pomocy, kontekst pomocy oraz identyfikator GUID interfejsu, który definiuje błąd (zawsze **GUID_NULL** dla klas .NET).|  
|**IProvideClassInfo**|Jeśli opakowany obiekt COM implementuje **IProvideClassInfo**, otoka wyodrębnia informacje o typie z tego interfejsu, aby zapewnić lepszą tożsamość typu.|  
|**IUnknown**|W przypadku tożsamości obiektu, przekształcenia typów i zarządzania okresem istnienia:<br /><br /> -Tożsamość obiektu<br />     Środowisko uruchomieniowe rozróżnia obiekty COM, porównując wartość interfejsu **IUnknown** dla każdego obiektu.<br />-Typ przekształcenia<br />     Otoka RCW rozpoznaje odnajdywanie typu dynamicznego wykonywane przez metodę **QueryInterface** .<br />— Zarządzanie okresem istnienia<br />     Przy użyciu metody **QueryInterface** , otoka pobiera i utrzymuje odwołanie do obiektu niezarządzanego, dopóki środowisko uruchomieniowe nie wykonuje wyrzucania elementów bezużytecznych w otoki, która zwalnia obiekt niezarządzany.|  
  
 Otoka (RCW) opcjonalnie wykorzystuje interfejsy wymienione w poniższej tabeli, które są udostępniane przez obiekt, który jest zawijany.  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|**IConnectionPoint** i **IConnectionPointContainer**|Otoka RCW Konwertuje obiekty, które uwidaczniają styl zdarzenia punktu połączenia do zdarzeń na podstawie delegowania.|  
|**IDispatchEx** (tylko .NET Framework) |Jeśli klasa implementuje **IDispatchEx**, otoka zawiera implementację **IExpando**. Interfejs **IDispatchEx** jest rozszerzeniem interfejsu **IDispatch** , który, w przeciwieństwie do **IDispatch**, włącza Wyliczenie, Dodawanie, usuwanie i uwzględnianie wielkości liter dla elementów członkowskich.|  
|**IEnumVARIANT**|Włącza typy COM obsługujące wyliczenia, które mają być traktowane jako kolekcje.|  
  
## <a name="see-also"></a>Zobacz też

- [Otoki COM](com-wrappers.md)
- [Wywoływana otoka COM](com-callable-wrapper.md)
- [Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Importowanie biblioteki typów jako zestawu](../../framework/interop/importing-a-type-library-as-an-assembly.md)
