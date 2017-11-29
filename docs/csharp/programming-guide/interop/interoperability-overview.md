---
title: "Przegląd współdziałania (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: de7ff105de85392fd4b8b342f26e67e89d0d9b96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
W temacie opisano metody, aby umożliwić współpracę między kodem C# zarządzanego i kodu niezarządzanego.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, że umożliwia zarządzanego kodu wywoływanie niezarządzanych funkcji, które zostały wdrożone w biblioteki dołączanej dynamicznie (dll), takich jak w interfejsie API Win32 firmy Microsoft. Lokalizuje i wywołuje wyeksportowanej funkcji i marshals granicy współdziałanie argumenty (liczby całkowite, ciągi, tablic, struktur i tak dalej), zgodnie z potrzebami.  
  
 Aby uzyskać więcej informacji, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [porady: użycie wywołania platformy do odtwarzania pliku Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywoływanie kodu niezarządzanego, która jest poza środowiskiem CLR pomija ten mechanizm zabezpieczeń i w związku z tym stanowi zagrożenie bezpieczeństwa. Na przykład kodu niezarządzanego może wywołać zasobów za pomocą kodu niezarządzanego bezpośrednio, pomijanie mechanizmy zabezpieczeń CLR. Aby uzyskać więcej informacji, zobacz [zabezpieczenia programu .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Międzyoperacyjności języka C++, znanej także jako ją po prostu działa (IJW), można użyć do zakodowania klasę natywnych języka C++, dzięki czemu mogą być używane przez kod, który został utworzony w języku C# lub innego języka .NET Framework. Aby to zrobić, można napisać kod C++ do opakowywania natywnej biblioteki DLL lub składnika COM. W przeciwieństwie do innych języków .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] ma współdziałanie obsługuje czy umożliwia zarządzanych i niezarządzanych kod aby się znajdować w tej samej aplikacji, a nawet w tym samym pliku. Następnie kompilowania kodu C++ za pomocą **/CLR** przełącznika kompilatora do tworzenia zarządzanego zestawu. Na koniec Dodaj odwołanie do zestawu w projekcie C# i używać opakowanej obiektów, tak jak w przypadku innych klas zarządzanych.  
  
## <a name="exposing-com-components-to-c"></a>Udostępnianie składników COM C#  
 Można używać składnika modelu COM z projektu C#. Ogólne kroki są następujące:  
  
1.  Zlokalizuj składnik COM i zarejestrowanie go. Użyj regsvr32.exe do rejestrowania lub wyrejestrowywania — rejestru biblioteki DLL modelu COM.  
  
2.  Dodaj do projektu odwołanie do biblioteki COM składnika lub typu.  
  
     Podczas dodawania odwołania, [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] używa [Tlbimp.exe (Importer biblioteki typów)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), który przyjmuje jako dane wejściowe do wyjściowego zestawu międzyoperacyjnego .NET Framework biblioteki typów. Zestaw o nazwie wywoływana otoka środowiska uruchomieniowego (otoki RCW), zawiera zarządzanej klasy i interfejsy, które otaczają klasy COM i interfejsów, które znajdują się w bibliotece typów. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3.  Tworzenie wystąpienia klasy, która jest zdefiniowana w otoki RCW. To z kolei tworzy wystąpienie obiektu COM.  
  
4.  Użyj obiektu tak samo, jak użyć innych obiektów zarządzanych. Gdy obiekt jest odzyskana przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM są również zwalniane z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników modelu COM aplikacji .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).  
  
## <a name="exposing-c-to-com"></a>Udostępnianie C# dla modelu COM  
 Klienci COM, jaką może wykorzystać C# typy, które zostały prawidłowo widoczne. Podstawowe kroki, aby ujawnić typów C# są następujące:  
  
1.  Dodaj atrybutów międzyoperacyjności w projekcie C#.  
  
     Możesz wprowadzić zestawu COM widoczne, modyfikując [!INCLUDE[csprcs](~/includes/csprcs-md.md)] właściwości projektu. Aby uzyskać więcej informacji, zobacz [informacji o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generowanie Biblioteka typów COM i zarejestruj go do użytku COM.  
  
     Można zmodyfikować [!INCLUDE[csprcs](~/includes/csprcs-md.md)] właściwości do automatycznego rejestrowania zestawu języka C# dla międzyoperacyjności z modelem COM projektu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]używa [Regasm.exe (narzędzie rejestracji zestawów)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)za pomocą `/tlb` przełącznik wiersza polecenia, który przyjmuje zarządzanego zestawu jako dane wejściowe, aby wygenerować biblioteki typów. Zawiera opis tego typu biblioteki `public` typów w zestawie i dodaje wpisy rejestru, aby tworzyć klientów modelu COM klasy zarządzanej.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników .NET Framework modelowi COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) i [klasa COM — przykład](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawianie wydajności międzyoperacyjności](http://go.microsoft.com/fwlink/?LinkId=99564)  
 [Wprowadzenie do COM Interop](http://go.microsoft.com/fwlink/?LinkId=112406)  
 [Organizowanie między zarządzanymi i niezarządzanymi kodu](http://go.microsoft.com/fwlink/?LinkId=112398)  
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/sd10k43k)  
 [Współdziałanie COM zaawansowane](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
