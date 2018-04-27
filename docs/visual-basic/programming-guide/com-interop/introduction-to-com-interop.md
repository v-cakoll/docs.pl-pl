---
title: Wprowadzenie do COM Interop (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5a13fabd729218dc2a980b9c63e153d17a140cce
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="introduction-to-com-interop-visual-basic"></a>Wprowadzenie do COM Interop (Visual Basic)
Składnik modelu COM (Object) umożliwia obiekt ujawnia jego działanie z innymi składnikami i umożliwia obsługę aplikacji. Aplikacje przeznaczone dla środowisko uruchomieniowe języka wspólnego (CLR) oferują wiele zalet, gdy obiekty COM zostały podstawowych w systemie Windows programowania dla wielu lat.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacje zastąpi po pewnym czasie te z modelu COM. Do tego czasu należy użyć obiektów lub tworzenia modelu COM za pomocą programu Visual Studio. Współdziałanie z COM, lub *COM interop*, pozwala na użycie istniejących obiektów COM podczas przechodzenia do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] we własnym tempie.  
  
 Za pomocą [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] do tworzenia składników modelu COM, można użyć współdziałanie z COM bez rejestrowania. Dzięki temu można kontrolować, która wersja biblioteki DLL jest włączona, gdy więcej niż jedna wersja jest zainstalowana na komputerze i umożliwia użytkownikom końcowym, użyj polecenia XCOPY lub FTP do skopiowania aplikacji do odpowiedniego katalogu na komputerze, gdzie mogą być uruchamiane. Aby uzyskać więcej informacji, zobacz [współdziałanie z COM bez rejestrowania](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Zarządzany kod i dane  
 Kod utworzonych dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nazywa się *kodu zarządzanego*i zawiera metadane, który jest używany przez środowisko CLR. Dane używane przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji jest nazywany *danych zarządzanych* ponieważ środowisko uruchomieniowe zarządza zadań związanych z danymi, takie jak przydzielanie i odzyskiwanie pamięci i wykonywania kontrola typów. Domyślnie program Visual Basic .NET korzysta z kodu zarządzanego i danych, ale można uzyskać dostępu do niezarządzanego kodu i danych obiektów COM za pomocą zestawów międzyoperacyjnych (opisana dalej na tej stronie).  
  
## <a name="assemblies"></a>Zestawy  
 Zestaw jest podstawowym blokiem konstrukcyjnym [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Jest to zbiór funkcji wbudowanych, wersji i wdrożonego jako jednostka pojedynczą implementacją zawierający co najmniej jeden plik. Każdy zestaw zawiera manifest zestawu.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Biblioteki typów i manifestów zestawu  
 Biblioteki typów opis właściwości obiektów COM, takich jak nazwy elementów członkowskich i typy danych. Manifesty wykonywać tej samej funkcji [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Obejmują one informacje na następujące tematy:  
  
-   Tożsamość zestawu, wersji, kultury i podpis cyfrowy.  
  
-   Pliki wchodzące w skład zestawu implementacji.  
  
-   Typy i zasobów, które tworzą zestaw. W tym te, które są eksportowane z niego.  
  
-   Zależności kompilacji na innych zestawów.  
  
-   Uprawnienia wymagane dla zestawu do poprawnego działania.  
  
 Aby uzyskać więcej informacji na temat zestawów i manifesty, zobacz [zestawy i Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importowanie i eksportowanie bibliotek typów  
 Visual Studio zawiera narzędzia Tlbimp, umożliwiający importowanie informacji z biblioteki typów do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Za pomocą narzędzia Narzędziatlbexp można wygenerować biblioteki typów z zestawów.  
  
 Informacje o Tlbimp i Narzędziatlbexp, zobacz [Tlbimp.exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md) i [Tlbexp.exe (Eksporter biblioteki typów)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjne  
 Zestawy międzyoperacyjne są [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kodem zestawy, które mostek między zarządzanych i niezarządzanych, Mapowanie elementów członkowskich obiektu COM na odpowiednik [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zarządzanych elementów członkowskich. Zestawy międzyoperacyjne utworzony przez program Visual Basic .NET obsługi wielu szczegółów pracy z obiektami COM, takich jak przekazywanie współdziałania.  
  
## <a name="interoperability-marshaling"></a>Organizowanie współdziałanie  
 Wszystkie [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacje mają zestaw typowych umożliwiających współdziałanie obiektów, niezależnie od języka programowania, który jest używany. Parametry i wartości zwracanych obiektów COM niekiedy używane typy danych, które różnią się od używanych w kodzie zarządzanym. *Organizowanie współdziałanie* się proces tworzenia pakietów parametrów i zwracanych wartości do typów danych równoważne przechodzą do i z obiektami COM. Aby uzyskać więcej informacji, zobacz [organizowanie międzyoperacyjne](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)  
 [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (eksporter biblioteki typów)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Marshaling międzyoperacyjny](../../../framework/interop/interop-marshaling.md)  
 [Współdziałanie z COM bez rejestrowania](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
