---
title: Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642927"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)
Jeśli chcesz użyć obiekty COM i .NET Framework w tej samej aplikacji, należy spełnić różnice w jaki sposób obiekty istnieją w pamięci. Obiekt .NET Framework znajduje się w pamięci zarządzanej — pamięci kontrolowane przez środowisko uruchomieniowe języka wspólnego — i mogą być przenoszone w czasie wykonywania, zgodnie z potrzebami. Obiekt COM znajduje się w pamięci niezarządzanej i przenieść do innej lokalizacji pamięci nie jest oczekiwane. Visual Studio i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] narzędzia do sterowania interakcji z tych zarządzanych i niezarządzanych składników. Aby uzyskać więcej informacji na temat kodu zarządzanego, zobacz [środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md).  
  
 Oprócz przy użyciu obiektów COM w aplikacjach .NET, ma może używać języka Visual Basic umożliwiające tworzenie obiektów dostępny z kodem niezarządzanym za pośrednictwem modelu COM.  
  
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
