---
title: Udostępnianie składników .NET do modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4380e97cf4d556248f42981b350160710f1dd8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051818"
---
# <a name="exposing-net-components-to-com"></a>Udostępnianie składników .NET do modelu COM

Pisanie typu .NET i używanie tego typu z kodu niezarządzanego to odrębne działania dla deweloperów. W tej sekcji opisano kilka wskazówek dotyczących pisania kodu zarządzanego, który współdziała z klientami COM:

- [Kwalifikowanie typów .NET do](../../standard/native-interop/qualify-net-types-for-interoperation.md)międzyoperacyjności.

     Wszystkie typy zarządzane, metody, właściwości, pola i zdarzenia, które mają zostać ujawnione w modelu COM, muszą być publiczne. Typy muszą mieć publiczny Konstruktor bez parametrów, który jest jedynym konstruktorem, który może być wywoływany przez COM.

- [Stosowanie atrybutów](../../standard/native-interop/apply-interop-attributes.md)międzyoperacyjnych.

     Atrybuty niestandardowe w kodzie zarządzanym mogą wzmocnić współdziałanie składnika.

- [Pakowanie zestawu dla modelu COM](packaging-an-assembly-for-com.md).

     Deweloperzy COM mogą wymagać podsumowania kroków związanych z odwołującymi się i wdrażaniem zestawów.

 Ponadto w tej sekcji przedstawiono zadania związane z zużywaniem typu zarządzanego z klienta COM.

## <a name="to-consume-a-managed-type-from-com"></a>Aby użyć typu zarządzanego z modelu COM

1. [Zarejestruj zestawy przy użyciu modelu COM](registering-assemblies-with-com.md).

     Typy w zestawie (i biblioteki typów) muszą być zarejestrowane w czasie projektowania. Jeśli Instalator nie rejestruje zestawu, poinstruuj deweloperów COM, aby korzystali z Regasm. exe.

2. [Odwołuj się do typów .NET z modelu COM](how-to-reference-net-types-from-com.md).

     Deweloperzy COM mogą odwoływać się do typów w zestawie przy użyciu tych samych narzędzi i technik, których używają dzisiaj.

3. [Wywoływanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).

     Deweloperzy COM mogą wywoływanie metod w obiekcie .NET w taki sam sposób, jak wywoływanie metod dla dowolnego typu niezarządzanego. Na przykład interfejs API funkcji **COCREATEINSTANCE** com aktywuje obiekty .NET.

4. [Wdróż aplikację na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).

     Zestaw o silnej nazwie można zainstalować w globalnej pamięci podręcznej zestawów i wymaga podpisu od jego wydawcy. Zestawy, które nie mają silnej nazwy, muszą być zainstalowane w katalogu aplikacji klienta.

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](index.md)
- [Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET](com-interop-sample-com-client-and-net-server.md)
