---
title: Organizowanie danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181371"
---
# <a name="marshaling-data-with-com-interop"></a>Organizowanie danych za pomocą modelu COM
Współdziałanie COM zapewnia obsługę zarówno przy użyciu obiektów COM z kodu zarządzanego, jak i uwidaczniania zarządzanych obiektów na platformie COM. Obsługa organizowania danych do i z COM jest obszerna i prawie zawsze zapewnia prawidłowe zachowanie organizowania.  
  
 Zestaw Windows SDK zawiera następujące narzędzia międzyoperacyjne COM:  
  
- [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), który konwertuje bibliotekę typów COM na zestaw międzyoperacyjny. Z tego zestawu międzyoperacyjnej usługi organizowania generuje otoki, które wykonują rozrządzania danych między pamięcią zarządzaną i niezarządzaną.  
  
- [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), który tworzy bibliotekę typów COM z zestawu i generuje otokę, która wykonuje kierowanie podczas wywoływania metody.  
  
 W poniższych sekcjach łącze do tematów, które opisują procesy dostosowywania otoki międzyop, gdy można (lub musi) dostarczyć organizatora dodatkowe informacje o typie.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Jak: Ręczne tworzenie otoków](how-to-create-wrappers-manually.md) W tym artykule opisano sposób ręcznego tworzenia otoki COM w zarządzanym kodzie źródłowym.

 [Instrukcje: migrowanie zarządzanego kodu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 W tym artykule opisano sposób migracji zarządzanego kodu DCOM do WCF dla najbardziej bezpiecznego rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Zawiera odpowiednie typy danych zarządzanych i niezarządzanych.  
  
 [Dostosowywanie otoki współusznezwalne COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 W tym artykule opisano, <xref:System.Runtime.InteropServices.MarshalAsAttribute> jak jawnie marshal typy danych przy użyciu atrybutu w czasie projektowania.  
  
 [Dostosowywanie otoki wywoławcze w czasie wykonywania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 W tym artykule opisano, jak dostosować zachowanie organizowania typów w zestawie międzyoperacyjnym i jak zdefiniować typy COM ręcznie.  
  
 [Zaawansowana interoperacyjność COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Zawiera łącza do więcej informacji na temat dołączania składników COM do aplikacji .NET Framework.  
  
 [Podsumowanie konwersji biblioteki zdań do biblioteki typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Opisuje zestaw do wpisywania procesu konwersji eksportu biblioteki.  
  
 [Podsumowanie konwersji biblioteki typów na podsumowanie konwersji zestawu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Zawiera opis biblioteki typów do procesu konwersji importu zestawu.  
  
 [Współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 W tym artykule opisano, które akcje są obsługiwane podczas korzystania z typów ogólnych dla współdziałania COM.
