---
title: Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 6e8b4eba40cc1872cb289ca120679bb951f2652a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022387"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)

Jeśli chcesz użyć obiekty COM i .NET Framework w tej samej aplikacji, które należy spełnić różnic, w jaki sposób obiekty istnieją w pamięci. Obiekt .NET Framework znajduje się w pamięci zarządzanej — pamięci kontrolowanej przez środowisko uruchomieniowe języka wspólnego — i mogą być przenoszone w czasie wykonywania, zgodnie z potrzebami. Obiekt COM znajduje się w pamięci niezarządzanej i nie oczekuje się można przenieść do innej lokalizacji w pamięci. Program Visual Studio i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewnia narzędzia umożliwiające kontrolowanie interakcji z nich zarządzane i niezarządzane składniki. Aby uzyskać więcej informacji na temat kodu zarządzanego, zobacz [środowiska uruchomieniowego języka wspólnego](../../../standard/clr.md).

Oprócz obiektów COM w aplikacjach platformy .NET, również możesz tworzyć obiekty dostępne z niezarządzanego kodu za pomocą modelu COM. za pomocą języka Visual Basic

Linki na tej stronie szczegółowo interakcje między obiektami COM i .NET Framework.

## <a name="related-sections"></a>Sekcje pokrewne

| | |
|---------|---------|
| [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md) | Zawiera łącza do tematów obejmujących współdziałanie COM w języku Visual Basic, m.in. COM obiekty ActiveX formantów, bibliotek Win32 dll, zarządzanych obiektów i dziedziczenia z obiektami COM. |
| [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md) | Krótko opisano niektóre problemy interakcji między kodem zarządzanym i niezarządzanym i zawiera łącza do dalszych badań. |
| [Otoki COM](../../../framework/interop/com-wrappers.md) | W tym artykule omówiono wywoływanych otok środowiska uruchomieniowego, które pozwalają kodowi zarządzanemu wywoływania metod modelu COM, i wywoływanych otok COM, dzięki czemu klienci COM do wywołania metody obiektu .NET. |
| [Zaawansowane współdziałanie modeli COM](../../../framework/interop/index.md) | Zawiera łącza do tematów obejmujących współdziałanie COM w odniesieniu do otoki, wyjątki, dziedziczenie, wątków, zdarzenia, konwersji i organizowanie. |
| [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | W tym artykule omówiono narzędzia którego można użyć do konwersji definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego. |