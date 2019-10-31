---
title: Organizowanie danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: 24fa390c94baaa0fe009ebe513f2eb7aa34d34fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113997"
---
# <a name="marshaling-data-with-com-interop"></a>Organizowanie danych za pomocą modelu COM
Współdziałanie modelu COM zapewnia obsługę zarówno obiektów COM z kodu zarządzanego, jak i Uwidacznianie obiektów zarządzanych w modelu COM. Obsługa przekazywania danych do i z modelu COM jest obszerna i prawie zawsze zapewnia prawidłowe zachowanie organizowania.  
  
 Windows SDK obejmuje następujące narzędzia międzyoperacyjności modelu COM:  
  
- [Importer biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md), który konwertuje bibliotekę typów com na zestaw międzyoperacyjny. Z tego zestawu usługa Marshaling Interop generuje otoki, które wykonują kierowanie danych między zarządzaną i niezarządzaną pamięcią.  
  
- [Eksporter biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md), który tworzy bibliotekę typów com z zestawu i generuje otokę wykonującą operacje organizowania podczas wywołań metod.  
  
 W poniższych sekcjach znajdują się łącza do tematów opisujących procesy dostosowywania otok międzyoperacyjnych, gdy użytkownik może (lub musi) dostarczyć Organizatorowi dodatkowe informacje o typie.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Instrukcje: ręczne tworzenie otok](how-to-create-wrappers-manually.md)   
Opisuje sposób ręcznego tworzenia otoki COM w zarządzanym kodzie źródłowym. 
 
 [Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 Opisuje sposób migrowania zarządzanego kodu DCOM do usługi WCF w celu zapewnienia najbezpieczniejszego rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Zapewnia odpowiednie zarządzane i niezarządzane typy danych.  
  
 [Dostosowywanie wywoływanych otok COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Opisuje, jak jawnie zorganizować typy danych przy użyciu atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute> w czasie projektowania.  
  
 [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Opisuje sposób dostosowywania zachowania związanego z kierowaniem typów w zestawie międzyoperacyjnym i sposób ręcznego definiowania typów COM.  
  
 [Zaawansowana współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Zawiera łącza do dodatkowych informacji na temat dołączania składników COM do aplikacji .NET Framework.  
  
 [Podsumowanie konwersji zestawu na bibliotekę typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Opisuje zestaw do procesu konwersji eksportu biblioteki typów.  
  
 [Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Opisuje proces konwersji biblioteki typów na import zestawu.  
  
 [Współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Opisuje, które akcje są obsługiwane w przypadku używania typów ogólnych do współdziałania z modelem COM.
