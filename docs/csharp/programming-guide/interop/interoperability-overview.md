---
title: Przegląd współdziałania — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 2c9eb2a8e6c2db8dc06ebe48ca6eb37d5cf638e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700734"
---
# <a name="interoperability-overview-c-programming-guide"></a>Przegląd współdziałania (Przewodnik programowania w języku C#)
W temacie opisano metody umożliwiające współdziałanie między kodem zarządzanym c# a kodem niezarządzanym.  
  
## <a name="platform-invoke"></a>Wywołanie platformy  
 *Wywołanie platformy* to usługa, która umożliwia kod zarządzany do wywoływania funkcji niezarządzanych, które są implementowane w bibliotekach łączy dynamicznych (DLL), takich jak te w interfejsie API systemu Microsoft Windows. Lokalizuje i wywołuje wyeksportowaną funkcję i organizuje jej argumenty (liczby całkowite, ciągi, tablice, struktury itd.) przez granicę współdziałania w razie potrzeby.  
  
Aby uzyskać więcej informacji, zobacz [Korzystanie z niezarządzanych funkcji dll](../../../framework/interop/consuming-unmanaged-dll-functions.md) i [Jak używać wywołania platformy do odtwarzania pliku WAV](./how-to-use-platform-invoke-to-play-a-wave-file.md).
  
> [!NOTE]
> [Czas wykonywania języka wspólnego](../../../standard/clr.md) (CLR) zarządza dostępem do zasobów systemowych. Wywołanie kodu niezarządzanego, który znajduje się poza clr omija ten mechanizm zabezpieczeń i w związku z tym stanowi zagrożenie bezpieczeństwa. Na przykład kod niezarządzany może wywoływać zasoby w kodzie niezarządzanym bezpośrednio, z pominięciem mechanizmów zabezpieczeń CLR. Aby uzyskać więcej informacji, zobacz [Zabezpieczenia w .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>międzyoperacyjność C++  
 Można użyć c++ interop, znany również jako It Just Works (IJW), aby zawijać natywnej klasy C++, dzięki czemu mogą być używane przez kod, który jest stworzony w języku C# lub innego języka .NET Framework. Aby to zrobić, należy napisać kod C++ do zawijania natywnej dll lub składnika COM. W przeciwieństwie do innych języków .NET Framework visual C++ ma obsługę współdziałania, która umożliwia zarządzany i niezarządzany kod znajduje się w tej samej aplikacji, a nawet w tym samym pliku. Następnie należy utworzyć kod C++ przy użyciu przełącznika kompilatora **/clr** do tworzenia zestawu zarządzanego. Na koniec należy dodać odwołanie do zestawu w projekcie Języka C# i używać opakowanych obiektów, tak jak można użyć innych klas zarządzanych.  
  
## <a name="exposing-com-components-to-c"></a>Wystawianie składników COM na c\#
 Składnik COM można używać z projektu C#. Ogólne kroki są następujące:  
  
1. Zlokalizuj składnik COM, aby go użyć i zarejestrować. Użyj regsvr32.exe, aby zarejestrować lub wyrejestrować dll COM.  
  
2. Dodaj do projektu odwołanie do składnika COM lub biblioteki typów.  
  
     Po dodaniu odwołania program Visual Studio używa [tlbimp.exe (Type Library Importer),](../../../framework/tools/tlbimp-exe-type-library-importer.md)który przyjmuje biblioteki typów jako dane wejściowe, do danych wyjściowych .NET Framework interop zestawu. Zestaw, również o nazwie wywoływane otoki wykonywania (RCW), zawiera klasy zarządzane i interfejsy, które zawijają klasy COM i interfejsy, które znajdują się w bibliotece typów. Visual Studio dodaje do projektu odwołanie do wygenerowanego zestawu.  
  
3. Utwórz wystąpienie klasy zdefiniowanej w RCW. To z kolei tworzy wystąpienie obiektu COM.  
  
4. Użyj obiektu tak samo, jak używasz innych obiektów zarządzanych. Gdy obiekt jest odzyskiwany przez wyrzucanie elementów bezużytecznych, wystąpienie obiektu COM jest również zwalniany z pamięci.  
  
 Aby uzyskać więcej informacji, zobacz [Wystawianie składników COM do .NET Framework](../../../framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Wystawianie języka C# na rzecz com  
 Klienci COM mogą korzystać z typów Języka C#, które zostały poprawnie uwidocznione. Podstawowe kroki, aby udostępnić typy Języka C# są następujące:  
  
1. Dodaj atrybuty współdziałania w projekcie Języka C#.  
  
     Można udostępnić com złożenia, modyfikując właściwości projektu Visual C#. Aby uzyskać więcej informacji, zobacz [Okno dialogowe Informacje o złożeniu](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2. Wygeneruj bibliotekę typów COM i zarejestruj ją do użycia com.  
  
     Można zmodyfikować właściwości projektu Visual C#, aby automatycznie zarejestrować zestaw C# dla współdziałania COM. Visual Studio używa [Regasm.exe (Narzędzie rejestracji zestawu)](../../../framework/tools/regasm-exe-assembly-registration-tool.md), przy użyciu przełącznika `/tlb` wiersza polecenia, który przyjmuje zarządzany zestaw jako dane wejściowe, aby wygenerować bibliotekę typów. Biblioteka tego typu `public` opisuje typy w zestawie i dodaje wpisy rejestru, dzięki czemu klienci COM mogą tworzyć klasy zarządzane.  
  
 Aby uzyskać więcej informacji, zobacz [Wystawianie składników .NET Framework do COM](../../../framework/interop/exposing-dotnet-components-to-com.md) i [przykładowej klasy COM](./example-com-class.md).  
  
## <a name="see-also"></a>Zobacz też

- [Poprawa wydajności interop](https://docs.microsoft.com/previous-versions/msp-n-p/ff647812%28v=pandp.10%29)
- [Wprowadzenie do interoperacyjności między COM i .NET](/office/client-developer/outlook/pia/introduction-to-interoperability-between-com-and-net)
- [Wprowadzenie do współoperacji COM w języku Visual Basic](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
- [Organizowanie między kodem zarządzanym i niezarządzanym](../../../framework/interop/interop-marshaling.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
- [Przewodnik programowania języka C#](../index.md)
