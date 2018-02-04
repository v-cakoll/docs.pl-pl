---
title: "Przegląd współdziałania (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f799f86c5dc597b0fe26197ab6321b9d3e82f664
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
W temacie opisano metody, aby umożliwić współpracę między kodem C# zarządzanego i kodu niezarządzanego.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, że umożliwia zarządzanego kodu wywoływanie niezarządzanych funkcji, które zostały wdrożone w biblioteki dołączanej dynamicznie (dll), takich jak w interfejsie API Win32 firmy Microsoft. Lokalizuje i wywołuje wyeksportowanej funkcji i marshals granicy współdziałanie argumenty (liczby całkowite, ciągi, tablic, struktur i tak dalej), zgodnie z potrzebami.  
  
 Aby uzyskać więcej informacji, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [porady: użycie wywołania platformy do odtwarzania pliku Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywoływanie kodu niezarządzanego, która jest poza środowiskiem CLR pomija ten mechanizm zabezpieczeń i w związku z tym stanowi zagrożenie bezpieczeństwa. Na przykład kodu niezarządzanego może wywołać zasobów za pomocą kodu niezarządzanego bezpośrednio, pomijanie mechanizmy zabezpieczeń CLR. Aby uzyskać więcej informacji, zobacz [zabezpieczenia programu .NET Framework](https://technet.microsoft.com/en-us/security/).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Międzyoperacyjności języka C++, znanej także jako ją po prostu działa (IJW), można użyć do zakodowania klasę natywnych języka C++, dzięki czemu mogą być używane przez kod, który został utworzony w języku C# lub innego języka .NET Framework. Aby to zrobić, można napisać kod C++ do opakowywania natywnej biblioteki DLL lub składnika COM. W przeciwieństwie do innych języków .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] ma współdziałanie obsługuje czy umożliwia zarządzanych i niezarządzanych kod aby się znajdować w tej samej aplikacji, a nawet w tym samym pliku. Następnie kompilowania kodu C++ za pomocą **/CLR** przełącznika kompilatora do tworzenia zarządzanego zestawu. Na koniec Dodaj odwołanie do zestawu w projekcie C# i używać opakowanej obiektów, tak jak w przypadku innych klas zarządzanych.  
  
## <a name="exposing-com-components-to-c"></a>Udostępnianie składników COM C#  
 Można używać składnika modelu COM z projektu C#. Ogólne kroki są następujące:  
  
1.  Zlokalizuj składnik COM i zarejestrowanie go. Użyj regsvr32.exe do rejestrowania lub wyrejestrowywania — rejestru biblioteki DLL modelu COM.  
  
2.  Dodaj do projektu odwołanie do biblioteki COM składnika lub typu.  
  
     Podczas dodawania odwołania, [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] używa [Tlbimp.exe (Importer biblioteki typów)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), który przyjmuje jako dane wejściowe do wyjściowego zestawu międzyoperacyjnego .NET Framework biblioteki typów. Zestaw o nazwie wywoływana otoka środowiska uruchomieniowego (otoki RCW), zawiera zarządzanej klasy i interfejsy, które otaczają klasy COM i interfejsów, które znajdują się w bibliotece typów. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3.  Tworzenie wystąpienia klasy, która jest zdefiniowana w otoki RCW. To z kolei tworzy wystąpienie obiektu COM.  
  
4.  Użyj obiektu tak samo, jak użyć innych obiektów zarządzanych. Gdy obiekt jest odzyskana przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM są również zwalniane z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników modelu COM aplikacji .NET Framework](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Udostępnianie C# dla modelu COM  
 Klienci COM, jaką może wykorzystać C# typy, które zostały prawidłowo widoczne. Podstawowe kroki, aby ujawnić typów C# są następujące:  
  
1.  Dodaj atrybutów międzyoperacyjności w projekcie C#.  
  
     Możesz wprowadzić zestawu COM widoczne, modyfikując [!INCLUDE[csprcs](~/includes/csprcs-md.md)] właściwości projektu. Aby uzyskać więcej informacji, zobacz [informacji o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generowanie Biblioteka typów COM i zarejestruj go do użytku COM.  
  
     Można zmodyfikować [!INCLUDE[csprcs](~/includes/csprcs-md.md)] właściwości do automatycznego rejestrowania zestawu języka C# dla międzyoperacyjności z modelem COM projektu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]używa [Regasm.exe (narzędzie rejestracji zestawów)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)za pomocą `/tlb` przełącznik wiersza polecenia, który przyjmuje zarządzanego zestawu jako dane wejściowe, aby wygenerować biblioteki typów. Zawiera opis tego typu biblioteki `public` typów w zestawie i dodaje wpisy rejestru, aby tworzyć klientów modelu COM klasy zarządzanej.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) i [klasa COM — przykład](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawianie wydajności międzyoperacyjności](https://msdn.microsoft.com/library/ms998551.aspx)  
 [Wprowadzenie do współdziałanie COM i .NET](https://msdn.microsoft.com/library/office/bb610378.aspx) [wprowadzenie do COM Interop w języku Visual Basic](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md) [organizowanie między zarządzanych i niezarządzanych kodu](../../../../docs/framework/interop/interop-marshaling.md)  
 [Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
