---
title: Wprowadzenie do COM Interop (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 5e31bfafdc321bb514ecdadd49b7e2c6adf53948
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262181"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Wprowadzenie do COM Interop (Visual Basic)
Component Object Model (COM) umożliwia obiektu udostępnić swoje funkcje z innymi składnikami i umożliwia obsługę aplikacji. Gdy obiekty COM zostały podstawowe znaczenie dla Windows programowania przez wiele lat, aplikacje przeznaczone do środowisko uruchomieniowe języka wspólnego (CLR) oferują wiele zalet.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacje zostanie ostatecznie zastąpią opracowanych za pomocą modelu COM. W tym czasie może mieć do użycia lub Utwórz obiekty COM za pomocą programu Visual Studio. Współdziałanie z COM, lub *COM interop*, pozwala na korzystanie z istniejących obiektów COM podczas przechodzenia do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] w swoim własnym tempie.  
  
 Za pomocą [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] do tworzenia składników modelu COM, można użyć Usługa międzyoperacyjna modelu COM bez rejestrowania. Dzięki temu można kontrolować, którą wersję biblioteki DLL jest włączona, gdy więcej niż jedna wersja jest zainstalowana na komputerze i umożliwia użytkownikom końcowym kopiowanie za pomocą polecenia XCOPY lub FTP aplikacji do odpowiedniego katalogu na komputerze, gdzie mogą być uruchamiane. Aby uzyskać więcej informacji, zobacz [współdziałania z modelem COM bez rejestrowania](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Zarządzany kod i dane  
 Kod opracowany dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nazywa się *kodu zarządzanego*i zawiera metadane, który jest używany przez środowisko CLR. Dane używane przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nosi nazwę aplikacji *danych zarządzanych* ponieważ środowisko uruchomieniowe zarządza zadań związanych z danymi, takich jak przydzielanie i odzyskiwanie pamięci i wykonywania sprawdzenie typu. Domyślnie program Visual Basic .NET korzysta z kodu zarządzanego i danych, ale możesz dostęp do niezarządzanego kodu i danych obiektów COM, przy użyciu zestawów międzyoperacyjnych (opisane dalej na tej stronie).  
  
## <a name="assemblies"></a>Zestawy  
 Zestaw jest elementem podstawowym składowym [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Jest to kolekcja funkcje, które są skompilowane, wersjonowane i wdrażane jako jednostka pojedynczą implementacją zawierające jeden lub więcej plików. Każdy zestaw zawiera manifest zestawu.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Manifesty zestawów i bibliotek typów  
 Biblioteki typów opis właściwości obiektów COM, takich jak nazwy elementów członkowskich i typy danych. Manifesty pełnią taką samą funkcję, aby uzyskać [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Ulepszenia obejmują następujące informacje:  
  
-   Tożsamość zestawu, wersji, kultury i podpisu cyfrowego.  
  
-   Pliki, które tworzą implementację zespołu.  
  
-   Typy i zasoby wchodzące w skład zestawu. W tym te, które są eksportowane z niego.  
  
-   Zależności kompilacji od innych zestawów.  
  
-   Uprawnienia wymagane dla zestawu, by działała poprawnie.  
  
 Aby uzyskać więcej informacji na temat zestawów i manifesty, zobacz [zestawy i Globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importowanie i eksportowanie bibliotek typów  
 Program Visual Studio zawiera narzędzia, Tlbimp, który umożliwia importowanie informacji z biblioteki typów do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji. Można generować biblioteki typów z zestawów przy użyciu narzędzia Narzędziatlbexp.  
  
 Aby uzyskać informacji na temat Tlbimp i Tlbexp, zobacz [Tlbimp.exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md) i [Tlbexp.exe (Eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjne  
 Są zestawy międzyoperacyjne [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kod zestawów, które Most między zarządzanych i niezarządzanych, elementach członkowskich obiektu COM mapowania na odpowiednik [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zarządzanych elementów członkowskich. Zestawy międzyoperacyjne utworzone przez program Visual Basic .NET obsługiwać wiele szczegółów pracy z obiektami COM, takie jak organizowanie współdziałania.  
  
## <a name="interoperability-marshaling"></a>Marshaling współdziałanie  
 Wszystkie [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacje mają zestaw popularne typy umożliwiające współdziałanie obiektów, niezależnie od języka programowania, który jest używany. Parametry i wartości zwracanych obiektów COM czasami wykorzystują typy danych, które różnią się od tych używanych w kodzie zarządzanym. *Marshaling współdziałanie* to proces tworzenia pakietów parametrów i zwracanych wartości na równoważne typy danych, przechodzące do i z obiektami COM. Aby uzyskać więcej informacji, zobacz [Marshaling międzyoperacyjności](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Zobacz także

- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
- [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)  
- [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
- [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
- [Tlbexp.exe (eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)  
- [Marshaling międzyoperacyjny](../../../framework/interop/interop-marshaling.md)  
- [Współdziałanie z COM bez rejestrowania](../../../framework/interop/registration-free-com-interop.md)
