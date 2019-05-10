---
title: Udostępnianie składników COM programowi.NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20ec022f378feba3368ea79fdd5c6ee7ecccf1b9
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469661"
---
# <a name="exposing-com-components-to-the-net-framework"></a>Udostępnianie składników COM programowi.NET Framework
Ta sekcja zawiera podsumowanie procesu potrzebne, aby udostępnić istniejący składnik COM do zarządzanego kodu. Aby uzyskać informacje na temat pisania serwerów COM, który jest ściśle zintegrowane z .NET Framework, zobacz [zagadnień projektowych dotyczących współdziałanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).
  
 Istniejących składników COM są cenne zasoby w zarządzanym kodzie jako aplikacje biznesowe warstwy środkowej lub funkcje izolowanego. Idealnym rozwiązaniem składnik zawiera podstawowy zestaw międzyoperacyjny i ściśle odpowiada programowania Standardy nakładane przez model COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>Aby udostępnić składników COM programowi .NET Framework  
  
1. [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md).  
  
     Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy modelu COM. Istnieje kilka sposobów, aby uzyskać zestaw zawierający typy modelu COM importowanych w metadanych.  
  
2. [Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).  
  
     Można sprawdzić typy modelu COM, aktywować wystąpienia i wywoływać metody na obiekt COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.  
  
3. [Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia kompilatory dla kilku języków zgodny z Common Language Specification (CLS), w tym Visual Basic C#, i C++.  
  
4. [Wdrażanie aplikacji międzyoperacyjnych](deploying-an-interop-application.md).  
  
     Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnej nazwie](../app-domains/strong-named-assemblies.md), podpisane zestawów w globalnej pamięci podręcznej.  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](index.md)
- [Zagadnienia dotyczące projektowania do celów międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [Przykład międzyoperacyjnego modelu COM: Klient modelu .NET i serwer COM](com-interop-sample-net-client-and-com-server.md)
- [Niezależność od języka i składniki niezależne od języka](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
