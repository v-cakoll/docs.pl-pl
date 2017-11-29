---
title: "Udostępnianie składników COM programowi.NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26efd43a05252e657626063d7dd04b1020dace18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-com-components-to-the-net-framework"></a>Udostępnianie składników COM programowi.NET Framework
Ta sekcja zawiera podsumowanie procesu potrzebne do udostępnienia istniejących składnika modelu COM z kodem zarządzanym. Aby uzyskać informacje na temat pisania serwerów COM to ściśle zintegrowane z programu .NET Framework, zobacz [projektowania współdziałanie](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).  
  
 Istniejące składniki COM są cenne zasoby pozostają dostępne w zarządzanym kodzie jako biznesowym warstwy środkowej aplikacje lub funkcje izolowanym. Składnik idealne ma podstawowego zestawu międzyoperacyjnego i ściśle zgodne ze standardami programowania narzucone przez COM.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>Aby udostępnić składników modelu COM aplikacji .NET Framework  
  
1.  [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).  
  
     Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy COM. Istnieje kilka sposobów można uzyskać zestawu zawierającego typów COM zaimportowana jako metadanych.  
  
2.  [Tworzenie typów COM w kodzie zarządzanym](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
     Można sprawdzić typów COM, aktywować wystąpień i wywołania metod w obiekcie COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.  
  
3.  [Kompilowanie projektu międzyoperacyjnego](../../../docs/framework/interop/compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Zapewnia kilka języków zgodne z wspólnego języka specyfikacji (ze specyfikacją CLS), łącznie z kompilatorów [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++.  
  
4.  [Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md).  
  
     Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), podpisany zestawów w globalnej pamięci podręcznej zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)  
 [Zagadnienia dotyczące projektowania dla współdziałanie](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer COM](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [Niezależność od języka i elementy niezależne od języka](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
