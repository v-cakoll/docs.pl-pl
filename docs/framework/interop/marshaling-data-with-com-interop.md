---
title: Organizowanie danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16f94e8b85a1bedb8b7791c2b7fcaf6d154ba1b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833526"
---
# <a name="marshaling-data-with-com-interop"></a>Organizowanie danych za pomocą modelu COM
Usługa międzyoperacyjna modelu COM zapewnia obsługę zarówno za pomocą obiektów COM z kodu zarządzanego i udostępnianie zarządzane obiekty do modelu COM. Obsługa kierowania danych do i z modelu COM są obszerne i prawie zawsze zawiera poprawne zachowanie organizowania.  
  
 Zestaw Windows Software Development Kit (SDK) obejmuje następujące narzędzia międzyoperacyjności modelu COM:  
  
- [Importer biblioteki (Tlbimp.exe) wpisz](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), która konwertuje bibliotece typów modelu COM do zestawu międzyoperacyjnego. Z tego zestawu międzyoperacyjnego marshaling usługi generuje otoki, które wykonują danych szeregowanie między zarządzanymi i niezarządzanymi pamięci.  
  
- [Eksporter biblioteki (Tlbexp.exe) wpisz](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), która generuje bibliotekę typów modelu COM z zestawu i generuje otoki, który wykonuje marshaling podczas wywołania metody.  
  
 Poniższe sekcje łącza do tematów opisujących procesy dostosowywania otoki międzyoperacyjny podczas mogą lub musi podawania organizator informacji o dodatkowych typach.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Instrukcje: Ręczne tworzenie otok](how-to-create-wrappers-manually.md)   
W tym artykule opisano sposób tworzenia otoki COM ręcznie w zarządzanym kodzie źródłowym. 
 
 [Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 W tym artykule opisano, jak przeprowadzić migrację zarządzanego kodu DCOM do WCF dla najbardziej bezpieczne rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Udostępnia odpowiednie typy danych zarządzanych i niezarządzanych.  
  
 [Dostosowywanie wywoływanych otok COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Opisuje sposób kieruje jawnie tego typów danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.  
  
 [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 W tym artykule opisano, jak dostosować zachowanie organizowania typów w zestaw międzyoperacyjny oraz sposób definiowania typów modelu COM ręcznie.  
  
 [Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Zawiera łącza do dodatkowych informacji o dołączaniu składników COM do aplikacji środowiska .NET Framework.  
  
 [Zestaw do wpisz biblioteki konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 W tym artykule opisano zestaw na typ procesu konwersji eksportu biblioteki.  
  
 [Biblioteki typów na zestaw konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 W tym artykule opisano biblioteki typów do procesu konwersji importowania zestawu.  
  
 [Międzyoperacyjne używanie typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 W tym artykule opisano akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.
