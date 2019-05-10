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
ms.openlocfilehash: 4a6c2b755b87f6f01f08f54a2f2fc567868dbb55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626350"
---
# <a name="exposing-net-framework-components-to-com"></a>Udostępnianie składników .NET Framework modelowi COM
Typ architektury .NET do zapisywania i używania tego typu z niezarządzanego kodu są różne działania, dla deweloperów. W tej sekcji opisano kilka porad dotyczących pisaniu kodu zarządzanego, który współdziała z klientami COM:  
  
- [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Wszystkie zarządzane typy, metody, właściwości, pola i zdarzenia, które chcesz udostępnić w COM muszą być publiczne. Typy muszą mieć publicznego konstruktora domyślnego, który jest tylko konstruktorem, który może być wywoływany za pomocą modelu COM.  
  
- [Stosowanie atrybutów międzyoperacyjności](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Niestandardowe atrybuty w kodzie zarządzanym może zwiększyć współdziałanie składnika.  
  
- [Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Deweloperzy COM może wymagać podsumowania etapy odwołujące się do i wdrażaniu zestawów.  
  
 Ponadto w tej sekcji wymieniono zadania związane z wykorzystywanie typu zarządzanego z klientem COM.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Korzystanie z typu zarządzanego z modelu COM  
  
1. [Rejestrowanie zestawów z modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Typy w zestawie (i biblioteki typów) musi być zarejestrowana w czasie projektowania. Jeśli Instalator nie rejestruje zestaw, poinstruuj deweloperom COM, należy użyć Regasm.exe.  
  
2. [Odwoływać się do typów .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Deweloperzy COM może odwoływać się typy w zestawie przy użyciu tych samych narzędzi i technik, które używają już dziś.  
  
3. [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).  
  
     Deweloperzy COM może wywoływać metody dla obiektu .NET taki sam sposób mogą wywoływać metody dla dowolnego typu niezarządzanego. Na przykład COM **CoCreateInstance** API aktywuje obiektów platformy .NET.  
  
4. [Wdrażanie aplikacji do dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).  
  
     Zestawu z silną nazwą, można zainstalować w globalnej pamięci podręcznej i wymaga podpisu od jego wydawcy. Zestawy, które nie są silną nazwę muszą być zainstalowane w katalogu aplikacji klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
- [Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
