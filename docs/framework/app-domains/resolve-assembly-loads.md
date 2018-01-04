---
title: "Rozwiązywanie załadowań zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb975b7ee8fdbba8435937fcb6f976d464db932
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="resolving-assembly-loads"></a>Rozwiązywanie załadowań zestawów
Platforma .NET Framework zapewnia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia dla aplikacji, które wymagają większej kontroli nad ładowania zestawu. Obsługa tego zdarzenia, aplikacja może załadować zestawu do kontekstu ładowania z poza zwykłych sondowania ścieżek, wybierz które z kilku wersji zestawu do załadowania, emisji dynamicznego zestawu i zwraca je i tak dalej. Ten temat zawiera wskazówki dotyczące obsługi <xref:System.AppDomain.AssemblyResolve> zdarzeń.  
  
> [!NOTE]
>  Rozwiązywanie załadowań zestawów w kontekstu reflection-only, użyj <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> zdarzeń zamiast tego.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak działa zdarzeń AssemblyResolve  
 Po dokonaniu rejestracji programu obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzeń, program obsługi jest wywoływane zawsze, gdy środowisko uruchomieniowe nie powiedzie się powiązać zestawu według nazwy. Na przykład następujące metody podczas wywoływania z kodu użytkownika może spowodować <xref:System.AppDomain.AssemblyResolve> się zdarzenia:  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenie metody, której pierwszy argument jest ciąg reprezentujący nazwę wyświetlaną zestawu do załadowania (czyli długość ciągu zwróconego przez <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości).  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenie metody, której pierwszy argument jest <xref:System.Reflection.AssemblyName> obiekt, który identyfikuje zestaw do załadowania.  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Przeciążenie metody.  
  
-   <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> Lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> przeciążenie metody, która tworzy wystąpienie obiektu w innej domenie aplikacji.  
  
### <a name="what-the-event-handler-does"></a>Co to jest program obsługi zdarzeń  
 Program obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzenie otrzymuje nazwę wyświetlaną zestawu do załadowania do <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> właściwości. Jeśli program obsługi nie może rozpoznać nazwę zestawu, zwraca wartość null (`Nothing` w języku Visual Basic `nullptr` w programie Visual C++).  
  
 Program obsługi, jeśli rozpoznaje nazwy zestawu go załadować i zwraca zestaw, który spełnia żądania. Poniżej opisano kilka przykładowych scenariuszy.  
  
-   Jeśli program obsługi zna lokalizacji wersji zestawu, można załadować zestawu za pomocą <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody, możesz wrócić załadowany zestaw w przypadku powodzenia.  
  
-   Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywane jako tablice typu byte, tablica bajtów można załadować przy użyciu jednej z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, które przyjmują tablicy bajtów.  
  
-   Program obsługi, można wygenerować zestawu dynamicznego i przywrócić go.  
  
> [!NOTE]
>  Program obsługi musi załadować zestawu do obciążenia w kontekście, w kontekście ładowania lub bez kontekstu. Jeśli program obsługi ładuje zestawu do kontekstu reflection-only przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> podejmować obciążenia metody, która wywołała <xref:System.AppDomain.AssemblyResolve> zakończy się niepowodzeniem.  
  
 Jest odpowiedzialny za program obsługi zdarzeń, aby zwrócić odpowiedniego zestawu. Program obsługi może przeanalizować składni nazwę wyświetlaną żądany zestaw, przekazując <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> wartości właściwości do <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktora. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć programu obsługi <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwości w celu określenia, czy bieżące żądanie dotyczy zależność innego zestawu. Te informacje mogą pomóc w identyfikacji zestawu, który będzie odpowiadał zależności.  
  
 Program obsługi zdarzeń może zwrócić innej wersji niż żądana wersja zestawu.  
  
 W większości przypadków zestawu, który jest zwracany przez program obsługi zostanie wyświetlony w kontekście ładowania, niezależnie od tego, program obsługi ładuje go do kontekstu. Na przykład, jeśli program obsługi używa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody próbę załadowania zestawu w kontekście ładowania z zestawu jest wyświetlany w kontekście ładowania, gdy program obsługi zwraca go. Jednak w przypadku następujących zestawu pojawia się bez kontekście podczas obsługi zwraca go:  
  
-   Program obsługi ładuje zestaw bez kontekstu.  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Właściwość nie jest zerowa.  
  
-   Żądanie zestawu (oznacza to, że zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwości) została załadowana bez kontekstu.  
  
 Aby uzyskać informacje o kontekstach, zobacz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> przeciążenie metody.  
  
 Wiele wersji tego samego zestawu mogą zostać załadowane do tej samej domenie aplikacji. Takie rozwiązanie nie jest zalecane, ponieważ może to prowadzić do typu przydziału problemów. Zobacz [najlepsze rozwiązania dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Co nie należy przeprowadzać programu obsługi zdarzeń  
 Podstawowe reguły obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenie jest, że nie należy zwracać zestawu nie rozpoznają. Podczas pisania program obsługi, należy wiedzieć, zestawy, które mogą spowodować się zdarzenia. Dla innych zestawów programu obsługi powinien zwrócić wartości null.  
  
> [!IMPORTANT]
>  Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> zdarzenia zestawów satelickich. Ta zmiana wpływa napisane dla starszej wersji programu .NET Framework, program obsługi zdarzeń, jeśli program obsługi próbuje rozpoznać wszystkich żądań obciążenia zestawu. Programy obsługi zdarzeń, które Ignoruj zestawy nie rozpoznają nie dotyczy tej zmiany: zwracają wartość null, a normalne mechanizmów powrotu zostaną wykonane.  
  
 Podczas ładowania zestawu, program obsługi zdarzeń nie może używać dowolnej z <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, które mogą spowodować <xref:System.AppDomain.AssemblyResolve> zdarzeń będzie zgłoszono cyklicznie, ponieważ może to prowadzić do przepełnienia stosu. (Zobacz listę podane wcześniej w tym temacie). Dzieje się tak nawet wtedy, gdy udostępniają obsługi dla żądania obciążenia wyjątków, ponieważ nie jest wyjątek do momentu zwrócono wszystkich procedur obsługi zdarzeń. W ten sposób, następujący kod powoduje przepełnienie stosu Jeśli `MyAssembly` nie znaleziono:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
