---
title: Przegląd współdziałania — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 1342711ca17b0d2bf5122f4c749514e3b96c9ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921819"
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
W temacie opisano metody umożliwiające włączenie współdziałania kodu C# zarządzanego i kodu niezarządzanego.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych, które są zaimplementowane w bibliotekach dołączanych dynamicznie (dll), takich jak te w interfejsie API systemu Microsoft Windows. Lokalizuje i wywołuje wyeksportowaną funkcję i kierującie jej argumentów (liczbami całkowitymi, ciągami, tablicami, strukturami itd.) w granicach międzyoperacyjnych, zgodnie z wymaganiami.  
  
 Aby uzyskać więcej informacji, zobacz Korzystanie z niezarządzanych [funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [instrukcje: Użyj wywołania platformy, aby odtworzyć plik](./how-to-use-platform-invoke-to-play-a-wave-file.md)Wave.  
  
> [!NOTE]
> [Środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywoływanie niezarządzanego kodu, który znajduje się poza środowiskiem CLR, pomija ten mechanizm zabezpieczeń i w związku z tym stanowi zagrożenie bezpieczeństwa. Na przykład kod niezarządzany może wywoływać zasoby bezpośrednio w kodzie niezarządzanym, pomijając mechanizmy zabezpieczeń środowiska CLR. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w programie .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Można użyć C++ międzyoperacyjności, znanego również jako tylko działa (IJW), aby otoczyć klasę C++ natywną, tak aby mogła być używana przez kod, który został C# utworzony w lub innym języku .NET Framework. W tym celu napiszesz C++ kod w celu zawinięcia NATYWNEJ biblioteki DLL lub składnika com. W przeciwieństwie do innych języków .NET Framework C++ Wizualizacja zapewnia obsługę współdziałania, która umożliwia zlokalizowany kod zarządzany i niezarządzany w tej samej aplikacji, a nawet w tym samym pliku. Następnie można skompilować C++ kod przy użyciu przełącznika kompilatora **/CLR** w celu utworzenia zestawu zarządzanego. Na koniec Dodaj odwołanie do zestawu w C# projekcie i użyj opakowanych obiektów tak samo jak w przypadku innych zarządzanych klas.  
  
## <a name="exposing-com-components-to-c"></a>Udostępnianie składników COM w języku C\#
 Można wykorzystać składnik COM z C# projektu. Ogólne czynności są następujące:  
  
1. Znajdź składnik COM, który ma być używany, i zarejestruj go. Użyj programu Regsvr32. exe do zarejestrowania lub wyrejestrowania biblioteki DLL COM.  
  
2. Dodaj do projektu odwołanie do składnika modelu COM lub biblioteki typów.  
  
     Po dodaniu odwołania program Visual Studio używa programu [Tlbimp. exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md), który przyjmuje bibliotekę typów jako dane wejściowe, aby wyprowadzić zestaw międzyoperacyjny .NET Framework. Zestaw, nazywany również otoką (otoka czasowa środowiska uruchomieniowego), zawiera zarządzane klasy i interfejsy, które zawijają klasy COM i interfejsy, które znajdują się w bibliotece typów. Program Visual Studio dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3. Utwórz wystąpienie klasy, która jest zdefiniowana w OTOKi. To z kolei tworzy wystąpienie obiektu COM.  
  
4. Użyj obiektu tak samo jak w przypadku używania innych obiektów zarządzanych. Gdy obiekt jest odzyskiwany przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM jest również zwalniane z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [Udostępnianie składników com do .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Uwidacznianie C# do modelu com  
 Klienci modelu COM mogą C# korzystać z typów, które zostały prawidłowo uwidocznione. Podstawowe kroki w celu udostępnienia C# typów są następujące:  
  
1. Dodaj atrybuty międzyoperacyjności C# do projektu.  
  
     Można sprawić, aby zestaw COM był widoczny przez modyfikację właściwości projektu wizualnego C# . Aby uzyskać więcej informacji, zobacz [okno dialogowe informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Wygeneruj bibliotekę typów modelu COM i zarejestruj ją pod kątem użycia COM.  
  
     Możesz zmodyfikować właściwości projektu C# wizualnego, aby automatycznie zarejestrować C# zestaw na potrzeby współdziałania z modelem com. Program Visual Studio używa programu [Regasm. exe (Narzędzie rejestracji zestawów)](../../../framework/tools/regasm-exe-assembly-registration-tool.md)przy użyciu `/tlb` przełącznika wiersza polecenia, który pobiera zarządzany zestaw jako dane wejściowe, aby wygenerować bibliotekę typów. Ta biblioteka typów opisuje `public` typy w zestawie i dodaje wpisy rejestru, aby klienci modelu COM mogli tworzyć klasy zarządzane.  
  
 Aby uzyskać więcej informacji, zobacz [Udostępnianie składników .NET Framework do modelu COM](../../../framework/interop/exposing-dotnet-components-to-com.md) i [przykładowej klasy com](./example-com-class.md).  
  
## <a name="see-also"></a>Zobacz także

- [Poprawianie wydajności międzyoperacyjności](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Wprowadzenie do współdziałania między modelami COM i .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Wprowadzenie do międzyoperacyjności modelu COM w Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Kierowanie między zarządzanym i niezarządzanym kodem](../../../framework/interop/interop-marshaling.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Przewodnik programowania w języku C#](../index.md)
