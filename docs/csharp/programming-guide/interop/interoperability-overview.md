---
title: Przegląd współdziałania — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 6546a379d6d851aafbced0931221dc19ca022a72
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241737"
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
W tym temacie opisano metody umożliwiające współdziałanie między kodem zarządzanym C# i niezarządzanym kodem.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych, które są zaimplementowane w bibliotekach dołączanych dynamicznie (dll), takich jak te w interfejsie API systemu Microsoft Windows. Lokalizuje i wywołuje wyeksportowaną funkcję i kierującie jej argumentów (liczbami całkowitymi, ciągami, tablicami, strukturami itd.) w granicach międzyoperacyjnych, zgodnie z wymaganiami.  
  
Aby uzyskać więcej informacji, zobacz Korzystanie z [niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [jak odtworzyć plik WAV przy użyciu wywołania platformy](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> [Środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywoływanie niezarządzanego kodu, który znajduje się poza środowiskiem CLR, pomija ten mechanizm zabezpieczeń i w związku z tym stanowi zagrożenie bezpieczeństwa. Na przykład kod niezarządzany może wywoływać zasoby bezpośrednio w kodzie niezarządzanym, pomijając mechanizmy zabezpieczeń środowiska CLR. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w programie .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Możesz użyć międzyoperacyjności języka C++, znanego również jako "tylko działa" (IJW), aby otoczyć natywną klasę C++, aby można było jej używać w kodzie, który jest tworzony w języku C# lub innym języku .NET. W tym celu należy napisać kod języka C++ do zawijania natywnej biblioteki DLL lub składnika COM. W przeciwieństwie do innych języków .NET, Visual C++ ma obsługę współdziałania, dzięki czemu kod zarządzany i niezarządzany można znaleźć w tej samej aplikacji, a nawet w tym samym pliku. Następnie można skompilować kod języka C++ przy użyciu przełącznika kompilatora **/CLR** w celu utworzenia zestawu zarządzanego. Na koniec Dodaj odwołanie do zestawu w projekcie w języku C# i użyj opakowanych obiektów tak samo jak w przypadku innych zarządzanych klas.  
  
## <a name="exposing-com-components-to-c"></a>Udostępnianie składników COM w języku C\#
 Można wykorzystać składnik COM z projektu C#. Ogólne kroki są następujące:  
  
1. Znajdź składnik COM, który ma być używany, i zarejestruj go. Użyj programu Regsvr32. exe do zarejestrowania lub wyrejestrowania biblioteki DLL COM.  
  
2. Dodaj do projektu odwołanie do składnika modelu COM lub biblioteki typów.  
  
     Po dodaniu odwołania program Visual Studio używa programu [Tlbimp. exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md), który przyjmuje bibliotekę typów jako dane wejściowe, aby wyprowadzić zestaw .NET Interop. Zestaw, nazywany również otoką (otoka czasowa środowiska uruchomieniowego), zawiera zarządzane klasy i interfejsy, które zawijają klasy COM i interfejsy, które znajdują się w bibliotece typów. Program Visual Studio dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3. Utwórz wystąpienie klasy, która jest zdefiniowana w OTOKi. To z kolei tworzy wystąpienie obiektu COM.  
  
4. Użyj obiektu tak samo jak w przypadku używania innych obiektów zarządzanych. Gdy obiekt jest odzyskiwany przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM jest również zwalniane z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [Udostępnianie składników com do .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Udostępnianie języka C# do modelu COM  
 Klienci modelu COM mogą korzystać z typów języka C#, które zostały prawidłowo uwidocznione. Podstawowe kroki w celu udostępnienia typów języka C# są następujące:  
  
1. Dodaj atrybuty międzyoperacyjności w projekcie w języku C#.  
  
     Można sprawić, aby zestaw COM był widoczny przez modyfikację właściwości projektu Visual C#. Aby uzyskać więcej informacji, zobacz [okno dialogowe informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Wygeneruj bibliotekę typów modelu COM i zarejestruj ją pod kątem użycia COM.  
  
     Możesz zmodyfikować właściwości projektu Visual C#, aby automatycznie zarejestrować zestaw C# dla współdziałania z modelem COM. Program Visual Studio używa programu [Regasm. exe (Narzędzie rejestracji zestawów)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)przy użyciu `/tlb` przełącznika wiersza polecenia, który pobiera zarządzany zestaw jako dane wejściowe, aby wygenerować bibliotekę typów. Ta biblioteka typów opisuje `public` typy w zestawie i dodaje wpisy rejestru, aby klienci modelu COM mogli tworzyć klasy zarządzane.  
  
 Aby uzyskać więcej informacji, zobacz [Udostępnianie składników .NET Framework do modelu COM](../../../framework/interop/exposing-dotnet-components-to-com.md) i [przykładowej klasy com](./example-com-class.md).  
  
## <a name="see-also"></a>Zobacz też

- [Poprawianie wydajności międzyoperacyjności](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Wprowadzenie do współdziałania między modelami COM i .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Wprowadzenie do międzyoperacyjności modelu COM w Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Kierowanie między zarządzanym i niezarządzanym kodem](../../../framework/interop/interop-marshaling.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Przewodnik programowania w języku C#](../index.md)
