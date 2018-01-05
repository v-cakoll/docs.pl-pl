---
title: "Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c84143e22f33f572447c50e33559a52469b181a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)
Jeśli chcesz użyć obiekty COM i .NET Framework w tej samej aplikacji, należy spełnić różnice w jaki sposób obiekty istnieją w pamięci. Obiekt .NET Framework znajduje się w pamięci zarządzanej — pamięci kontrolowane przez środowisko uruchomieniowe języka wspólnego — i mogą być przenoszone w czasie wykonywania, zgodnie z potrzebami. Obiekt COM znajduje się w pamięci niezarządzanej i przenieść do innej lokalizacji pamięci nie jest oczekiwane. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] narzędzia do sterowania interakcji z tych zarządzanych i niezarządzanych składników. Aby uzyskać więcej informacji na temat kodu zarządzanego, zobacz [środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md).  
  
 Oprócz przy użyciu obiektów COM w aplikacjach .NET, ma może być [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umożliwiające tworzenie obiektów dostępny z kodem niezarządzanym za pośrednictwem modelu COM.  
  
 Linki na tej stronie zawierają szczegółowe informacje o interakcjach między obiektami COM i .NET Framework.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Zawiera łącza do tematów obejmujących współdziałanie COM w języku Visual Basic, w tym modelu COM obiektów, ActiveX formantów, biblioteki DLL systemu Win32, zarządzanych obiektów i dziedziczenia z obiektami COM.  
  
 [COM Interop Wrapper — błąd](/cpp/misc/com-interop-wrapper-error)  
 Opisuje skutki i opcje, czy system projektu nie może utworzyć otoka współdziałania COM dla poszczególnych składników.  
  
 [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)  
 Krótko opisano niektóre problemy interakcji między zarządzanymi i niezarządzanymi kodu i linki do dalszych badań.  
  
 [Otoki COM](../../../framework/interop/com-wrappers.md)  
 W tym artykule omówiono wywoływane otoki środowiska uruchomieniowego, które umożliwiają kodu zarządzanego do wywołania metody modelu COM, i wywoływane otoki COM, które umożliwiają klientom COM wywoływanie metody obiektu .NET.  
  
 [Współdziałanie COM zaawansowane](../../../framework/interop/index.md)  
 Zawiera łącza do tematów obejmujących współdziałanie COM względem otoki, wyjątki dziedziczenia, wątki, zdarzenia, konwersje i organizowanie.  
  
 [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 W tym artykule omówiono narzędzie, które umożliwia konwertowanie definicji typu znaleziony w Biblioteka typów COM na równoważne definicje w zestawie środowiska uruchomieniowego języka wspólnego.
