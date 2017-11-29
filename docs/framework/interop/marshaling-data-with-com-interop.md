---
title: "Marshaling danych za pomocą modelu COM"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a>Marshaling danych za pomocą modelu COM
Współdziałanie z COM zapewnia obsługę zarówno przy użyciu obiektów COM z kodu zarządzanego i udostępnianie zarządzane obiekty do modelu COM. Obsługa przekazywanie danych do i z modelu COM jest rozbudowana i prawie zawsze zawiera poprawne zachowanie marshalingu.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obejmuje następujące narzędzia międzyoperacyjnego COM:  
  
-   [Importer biblioteki (Tlbimp.exe) wpisz](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), który konwertuje Biblioteka typów COM do zestawu międzyoperacyjnego. Z tego zestawu interop organizowanie usługi generuje otoki wykonujących przekazywanie między zarządzanymi i niezarządzanymi pamięci danych.  
  
-   [Eksporter biblioteki (Tlbexp.exe) wpisz](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), która tworzy bibliotekę typów COM z zestawu i generuje otoki, który wykonuje przekazywanie podczas wywołania metody.  
  
 Poniższe sekcje łącza do tematów opisujących procesów dostosowywania otoki międzyoperacyjnego, jeśli można lub musi podasz organizatora typu dodatkowe informacje.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Porady: ręczne tworzenie otok](how-to-create-wrappers-manually.md)   
Opisuje sposób tworzenia otoki COM ręcznie w kodzie źródłowym zarządzanych. 
 
 [Porady: Migrowanie zarządzanego kodu DCOM do WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Opisuje sposób Migrowanie zarządzanego kodu DCOM do WCF dla najbardziej bezpieczne rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy danych modelu COM](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)  
 Zawiera odpowiednie typy zarządzane i niezarządzane danych.  
  
 [Dostosowywanie wywoływane otoki COM](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)  
 Opisuje sposób jawnie kierować typy danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.  
  
 [Dostosowywanie wywoływane otoki środowiska uruchomieniowego](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)  
 Opisuje sposób dostosować zachowanie marshalingu typów z zestawu międzyoperacyjnego oraz definiowanie typów COM ręcznie.  
  
 [Współdziałanie COM zaawansowane](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)  
 Zawiera łącza do dodatkowych informacji o włączenie składniki modelu COM aplikacji .NET Framework.  
  
 [Zestaw do typu biblioteki konwersja — podsumowanie](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)  
 Zawiera opis zestawu na typ procesu konwersji eksportu biblioteki.  
  
 [Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)  
 W tym artykule opisano bibliotekę typów, aby proces konwersji importu zestawu.  
  
 [Współdziałanie za pomocą typów ogólnych](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)  
 Opisuje akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.
