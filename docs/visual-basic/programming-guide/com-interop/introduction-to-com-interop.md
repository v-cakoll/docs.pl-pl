---
title: Wprowadzenie do usługi międzyoperacyjnej modelu COM
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 6c7caf266514c43e40135b33d848a688546acf1c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396782"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Wprowadzenie do COM Interop (Visual Basic)
Component Object Model (COM) umożliwia obiektowi uwidocznienie jego funkcjonalności innym składnikom i hostowanie aplikacji. Chociaż obiekty COM mają podstawowe znaczenie dla programowania systemu Windows przez wiele lat, aplikacje zaprojektowane dla środowiska uruchomieniowego języka wspólnego (CLR) oferują wiele korzyści.  
  
 Aplikacje .NET Framework będą ostatecznie zastępować te opracowane z modelem COM. Do tego czasu może być konieczne użycie lub utworzenie obiektów COM przy użyciu programu Visual Studio. Współdziałanie z modelami COM i *com Interop*umożliwia korzystanie z istniejących obiektów com podczas przejścia do .NET Framework we własnym tempie.  
  
 Za pomocą .NET Framework do tworzenia składników modelu COM można korzystać z międzyoperacyjności modelu COM bez rejestracji. Dzięki temu można kontrolować, która wersja biblioteki DLL jest włączona, gdy na komputerze jest zainstalowana więcej niż jedna wersja, i umożliwia użytkownikom końcowym używanie polecenia XCOPY lub FTP do kopiowania aplikacji do odpowiedniego katalogu na komputerze, na którym można uruchomić. Aby uzyskać więcej informacji, zobacz [niezależna od rejestracji model COM Interop](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Kod zarządzany i dane  
 Kod opracowany dla .NET Framework jest nazywany *kodem zarządzanym*i zawiera metadane, który jest używany przez środowisko CLR. Dane używane przez aplikacje .NET Framework są nazywane *danymi zarządzanymi* , ponieważ środowisko uruchomieniowe zarządza zadaniami związanymi z danymi, takimi jak przydzielanie i odzyskiwanie pamięci i wykonywanie kontroli typu. Domyślnie program Visual Basic .NET używa kodu zarządzanego i danych, ale można uzyskać dostęp do niezarządzanego kodu i danych obiektów COM przy użyciu zestawów międzyoperacyjnych (opisanych dalej na tej stronie).  
  
## <a name="assemblies"></a>Zestawy  
 Zestaw jest głównym blokiem konstrukcyjnym aplikacji .NET Framework. Jest to kolekcja funkcji, która jest skompilowana, w wersji i wdrożona jako jedna jednostka implementacji zawierająca jeden lub więcej plików. Każdy zestaw zawiera manifest zestawu.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Biblioteki typów i manifesty zestawów  
 Biblioteki typów opisują cechy obiektów COM, takich jak nazwy elementów członkowskich i typy danych. Manifesty zestawu wykonują tę samą funkcję dla .NET Framework aplikacji. Obejmują one następujące informacje:  
  
- Tożsamość zestawu, wersja, kultura i podpis cyfrowy.  
  
- Pliki wchodzące w skład implementacji zestawu.  
  
- Typy i zasoby wchodzące w skład zestawu. Obejmuje to te, które są eksportowane z tego programu.  
  
- Zależności czasu kompilacji dla innych zestawów.  
  
- Uprawnienia wymagane do poprawnego działania zestawu.  
  
 Aby uzyskać więcej informacji na temat zestawów i manifestów zestawów, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importowanie i eksportowanie bibliotek typów  
 Program Visual Studio zawiera narzędzie Tlbimp, które umożliwia importowanie informacji z biblioteki typów do aplikacji .NET Framework. Można generować biblioteki typów z zestawów za pomocą narzędzia Tlbexp.  
  
 Aby uzyskać informacje na temat Tlbimp i Tlbexp, zobacz [Tlbimp. exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md) i [Tlbexp. exe (Eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjności  
 Zestawy międzyoperacyjności są zestawami .NET Framework, które są mostkiem między zarządzanym i niezarządzanym kodem, i mapują elementy członkowskie obiektów COM na równoważne .NET Framework zarządzane elementy Zestawy międzyoperacyjności utworzone przez Visual Basic .NET obsługują wiele szczegółów pracy z obiektami COM, takich jak kierowanie współdziałania.  
  
## <a name="interoperability-marshaling"></a>Kierowanie współdziałania  
 Wszystkie aplikacje .NET Framework korzystają z zestawu wspólnych typów, które umożliwiają współdziałanie obiektów, niezależnie od używanego języka programowania. Parametry i zwracane wartości obiektów COM czasami używają typów danych, które różnią się od tych używanych w kodzie zarządzanym. *Kierowanie współdziałania* to proces pakowania parametrów i zwracania wartości do równoważnych typów danych podczas ich przenoszenia do i z obiektów com. Aby uzyskać więcej informacji, zobacz [organizowanie międzyoperacyjnych](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Zobacz też

- [Międzyoperacyjność modelu COM](index.md)
- [Przewodnik: Implementowanie dziedziczenia z obiektami COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Rozwiązywanie problemów związanych z współdziałaniem](troubleshooting-interoperability.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Tlbimp. exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp. exe (Eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Organizowanie międzyoperacyjne](../../../framework/interop/interop-marshaling.md)
- [Współdziałanie z modelem COM bez rejestrowania](../../../framework/interop/registration-free-com-interop.md)
