---
title: Przegląd współdziałania (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 747b2d420beeb63b89b21dd16d2977d12bc5d580
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244192"
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
Temacie opisano metody, aby umożliwić współdziałanie kodu języka C# zarządzanego i niezarządzanego kodu.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, że umożliwia zarządzanemu kodowi wywoływanie funkcji niezarządzanych, które są implementowane w biblioteki dołączanej dynamicznie (dll), takich jak w programie Microsoft Win32 API. Lokalizuje i wywołuje eksportowanych funkcji i kieruje argumentów (liczby całkowite, ciągi, tablice, struktur i tak dalej) wewnątrz międzyoperacyjnej granicy, zgodnie z potrzebami.  
  
 Aby uzyskać więcej informacji, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [porady: użycie wywołania platformy do odtwarzania pliku Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Środowiska uruchomieniowego języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywoływanie niezarządzanego kodu, który znajduje się poza środowisko CLR pomija ten mechanizm bezpieczeństwa, a w związku z tym może stanowić zagrożenie bezpieczeństwa. Na przykład kodu niezarządzanego może wywołać zasoby w niezarządzanym kodzie bezpośrednio z pominięciem mechanizmów zabezpieczeń CLR. Aby uzyskać więcej informacji, zobacz [zabezpieczeń .NET Framework](https://technet.microsoft.com/en-us/security/).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Za pomocą międzyoperacyjności języka C++, znany także jako ją po prostu działa (IJW), do opakowania natywnych klasy języka C++, dzięki czemu mogą być używane przez kod, który został utworzony w języku C# lub innym języku .NET Framework. Aby to zrobić, pisanie kodu C++, aby opakować natywnej biblioteki DLL lub składnika COM. W przeciwieństwie do innych językach .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] ma współdziałanie pomocy technicznej, że umożliwia kodu zarządzanego i niezarządzanego zlokalizowanym w tej samej aplikacji, a nawet w tym samym pliku. Następnie utworzysz kodu C++ za pomocą **/CLR** przełącznika kompilatora, aby utworzyć zestaw zarządzany. Na koniec Dodaj odwołanie do zestawu w projekcie języka C# i używać opakowanej obiektów, tak jak w przypadku innych klas zarządzanych.  
  
## <a name="exposing-com-components-to-c"></a>Udostępnianie składników COM do języka C#  
 Mogą wykorzystywać składnika modelu COM z projektu języka C#. Ogólne kroki są następujące:  
  
1.  Zlokalizuj składnik COM, aby użyć i zarejestrować ją. Użyj regsvr32.exe zarejestrować lub wyrejestrować — Zarejestruj bibliotekę DLL modelu COM.  
  
2.  Dodaj do projektu odwołanie do biblioteki modelu COM składnika lub typu.  
  
     Po dodaniu odwołania, program Visual Studio używa [Tlbimp.exe (Importer biblioteki typów)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), który przyjmuje jako dane wejściowe do wyjściowego zestawu międzyoperacyjnego .NET Framework bibliotekę typów. Zestaw o nazwie wywoływana otoka środowiska uruchomieniowego (RCW) zawiera zarządzanych klas i interfejsów, które umieszczają w otoce klasy COM i interfejsy, które znajdują się w bibliotece typów. Visual Studio dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3.  Tworzenie wystąpienia klasy, która jest zdefiniowana w RCW. Spowoduje to, z kolei utworzenie wystąpienia obiektu COM.  
  
4.  Użyj obiektu, tak samo, jak używać innych obiektów zarządzanych. Gdy obiekt jest odzyskiwane przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM jest również zwalniane z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników modelu COM aplikacji .NET Framework](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Udostępnianie C# dla modelu COM  
 Klienci COM mogą wykorzystywać C# typy, które zostały poprawnie udostępniane. Podstawowe kroki, aby uwidocznić typów języka C# są następujące:  
  
1.  Dodawanie atrybutów międzyoperacyjności w projekcie języka C#.  
  
     Zestaw COM można uwidocznić, modyfikując właściwości projektu Visual C#. Aby uzyskać więcej informacji, zobacz [informacje o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generuj bibliotekę typów modelu COM i zarejestruj je dla modelu COM użycia.  
  
     Można zmodyfikować właściwości projektu Visual C# do automatycznego rejestrowania zestawu języka C# dla współdziałania z modelem COM. Program Visual Studio używa [Regasm.exe (narzędzie rejestracji zestawów)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)przy użyciu `/tlb` przełącznik wiersza polecenia, które pobiera zestaw zarządzany jako dane wejściowe, aby wygenerować bibliotekę typów. Ta biblioteka typów zawiera opis `public` typy w zestawie i dodaje wpisy rejestru, dzięki czemu klienci COM mogą tworzyć klas zarządzanych.  
  
 Aby uzyskać więcej informacji, zobacz [udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) i [klasa COM — przykład](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawa wydajności międzyoperacyjności](https://msdn.microsoft.com/library/ms998551.aspx)  
 [Wprowadzenie do współdziałania między COM i .NET](https://msdn.microsoft.com/library/office/bb610378.aspx)  
 [Wprowadzenie do COM Interop w języku Visual Basic](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 [Szeregowanie między kodem zarządzanym i niezarządzanym](../../../../docs/framework/interop/interop-marshaling.md)  
 [Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
