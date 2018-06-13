---
title: Udostępnianie składników .NET Framework modelowi COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f11928388dba9b0e9b442578bfb7b6f751c2e172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387435"
---
# <a name="exposing-net-framework-components-to-com"></a>Udostępnianie składników .NET Framework modelowi COM
Typ architektury .NET do zapisu i korzystanie z tego typu z kodem niezarządzanym są różne działania dla deweloperów. W tej sekcji opisano kilka porady dotyczące pisania zarządzanego kodu, który współdziała z klientami COM:  
  
-   [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Wszystkie zarządzane typy, metody, właściwości, pól i zdarzenia, które ma zostać udostępniona modelowi COM muszą być publiczne. Typy musi mieć domyślnego konstruktora publicznego, który jest jedynym Konstruktor, który można wywołać za pomocą modelu COM.  
  
-   [Stosowanie atrybutów międzyoperacyjności](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Atrybuty niestandardowe w kod zarządzany może zwiększyć współdziałanie składnika.  
  
-   [Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Deweloperzy COM może wymagać zawierają podsumowanie etapy odwołujące się do i wdrażanie z zestawów.  
  
 Ponadto w tej sekcji wymieniono zadania związane z korzystanie z klient modelu COM typu zarządzanego.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Aby korzystać z modelu COM typu zarządzanego  
  
1.  [Rejestrowanie zestawów w modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Typy w zestawie (i biblioteki typów) musi być zarejestrowana w czasie projektowania. Jeśli Instalator nie rejestruje zestaw, poinstruuj COM deweloperom używanie Regasm.exe.  
  
2.  [Odwoływać się do typów .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Deweloperzy COM może odwoływać się do typów w zestawie przy użyciu tego samego narzędzi i technik, których używają obecnie.  
  
3.  [Wywołanie obiektu .NET](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).  
  
     Deweloperzy COM można wywoływać metod w obiektu .NET. ten sam sposób ich wywoływać metod w dowolnego typu niezarządzanego. Na przykład COM **wywołanie funkcji CoCreateInstance** interfejsu API aktywuje obiekty .NET.  
  
4.  [Wdrażanie aplikacji modelu COM dostępu](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).  
  
     Zestawu z silną nazwą można zainstalować w pamięci podręcznej GAC i wymaga podpisu od jego wydawcy. Zestawy, które nie są silne nazwy musi być zainstalowany w katalogu aplikacji klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)  
 [Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
