---
title: Wprowadzenie do COM Interop (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 5eb862d75f8870da40af4cd817fa32a3d2781f38
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592720"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Wprowadzenie do COM Interop (Visual Basic)
Component Object Model (COM) umożliwia obiektu udostępnić swoje funkcje z innymi składnikami i umożliwia obsługę aplikacji. Gdy obiekty COM zostały podstawowe znaczenie dla Windows programowania przez wiele lat, aplikacje przeznaczone do środowisko uruchomieniowe języka wspólnego (CLR) oferują wiele zalet.  
  
 Aplikacje programu .NET framework zostanie ostatecznie zastąpią opracowanych za pomocą modelu COM. W tym czasie może mieć do użycia lub Utwórz obiekty COM za pomocą programu Visual Studio. Współdziałanie z COM, lub *COM interop*, pozwala na korzystanie z istniejących obiektów COM podczas przechodzenia do programu .NET Framework w swoim własnym tempie.  
  
 Za pomocą programu .NET Framework do tworzenia składników modelu COM, można użyć Usługa międzyoperacyjna modelu COM bez rejestrowania. Dzięki temu można kontrolować, którą wersję biblioteki DLL jest włączona, gdy więcej niż jedna wersja jest zainstalowana na komputerze i umożliwia użytkownikom końcowym kopiowanie za pomocą polecenia XCOPY lub FTP aplikacji do odpowiedniego katalogu na komputerze, gdzie mogą być uruchamiane. Aby uzyskać więcej informacji, zobacz [współdziałania z modelem COM bez rejestrowania](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Zarządzany kod i dane  
 Kod opracowany dla programu .NET Framework jest określane jako *kodu zarządzanego*i zawiera metadane, który jest używany przez środowisko CLR. Dane używane przez aplikacje programu .NET Framework są nazywane *danych zarządzanych* ponieważ środowisko uruchomieniowe zarządza zadań związanych z danymi, takich jak przydzielanie i odzyskiwanie pamięci i wykonywania sprawdzenie typu. Domyślnie program Visual Basic .NET korzysta z kodu zarządzanego i danych, ale możesz dostęp do niezarządzanego kodu i danych obiektów COM, przy użyciu zestawów międzyoperacyjnych (opisane dalej na tej stronie).  
  
## <a name="assemblies"></a>Zestawy  
 Zestaw jest podstawowy składnik aplikacji .NET Framework. Jest to kolekcja funkcje, które są skompilowane, wersjonowane i wdrażane jako jednostka pojedynczą implementacją zawierające jeden lub więcej plików. Każdy zestaw zawiera manifest zestawu.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Manifesty zestawów i bibliotek typów  
 Biblioteki typów opis właściwości obiektów COM, takich jak nazwy elementów członkowskich i typy danych. Manifesty pełnią taką samą funkcję dla aplikacji .NET Framework. Ulepszenia obejmują następujące informacje:  
  
- Tożsamość zestawu, wersji, kultury i podpisu cyfrowego.  
  
- Pliki, które tworzą implementację zespołu.  
  
- Typy i zasoby wchodzące w skład zestawu. W tym te, które są eksportowane z niego.  
  
- Zależności kompilacji od innych zestawów.  
  
- Uprawnienia wymagane dla zestawu, by działała poprawnie.  
  
 Aby uzyskać więcej informacji na temat zestawów i manifesty, zobacz [zestawy na platformie .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importowanie i eksportowanie bibliotek typów  
 Program Visual Studio zawiera narzędzia, Tlbimp, w którym można zaimportować informacje z biblioteki typów do aplikacji autonomicznej .NET Framework. Można generować biblioteki typów z zestawów przy użyciu narzędzia Narzędziatlbexp.  
  
 Aby uzyskać informacji na temat Tlbimp i Tlbexp, zobacz [Tlbimp.exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md) i [Tlbexp.exe (Eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjne  
 Zestawy międzyoperacyjne są zestawów .NET Framework, które Most między zarządzane i kod niezarządzany, mapowanie elementach członkowskich obiektu modelu COM do równoważnych .NET Framework zarządzanych elementów członkowskich. Zestawy międzyoperacyjne utworzone przez program Visual Basic .NET obsługiwać wiele szczegółów pracy z obiektami COM, takie jak organizowanie współdziałania.  
  
## <a name="interoperability-marshaling"></a>Marshaling współdziałanie  
 Wszystkie aplikacje programu .NET Framework mają zestaw popularne typy umożliwiające współdziałanie obiektów, niezależnie od języka programowania, który jest używany. Parametry i wartości zwracanych obiektów COM czasami wykorzystują typy danych, które różnią się od tych używanych w kodzie zarządzanym. *Marshaling współdziałanie* to proces tworzenia pakietów parametrów i zwracanych wartości na równoważne typy danych, przechodzące do i z obiektami COM. Aby uzyskać więcej informacji, zobacz [Marshaling międzyoperacyjności](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Zobacz także

- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Przewodnik: implementowanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Marshaling międzyoperacyjny](../../../framework/interop/interop-marshaling.md)
- [Współdziałanie z COM bez rejestrowania](../../../framework/interop/registration-free-com-interop.md)
