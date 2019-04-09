---
title: Rozwiązywanie załadowań zestawów
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: accb06421b8a697b0ee89adab0a9dffa23cffb05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193112"
---
# <a name="resolving-assembly-loads"></a>Rozwiązywanie załadowań zestawów
Program .NET Framework oferuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia dla aplikacji wymagających większej kontroli nad ładowania zestawu. Obsługa tego zdarzenia, aplikacja może załadowania zestawu w kontekstu ładowania z poza normalny sondowania ścieżek, wybierz której z kilku wersji zestawu do załadowania, emitują zestawu dynamicznego i przywrócić go i tak dalej. Ten temat zawiera wskazówki dotyczące obsługi <xref:System.AppDomain.AssemblyResolve> zdarzeń.  
  
> [!NOTE]
>  Rozwiązywanie załadowań zestawów w kontekstu reflection-only, użyj <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> zdarzeń zamiast tego.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak działa zdarzeń AssemblyResolve  
 Podczas rejestrowania procedury obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzeń, program obsługi jest wywoływana zawsze wtedy, gdy środowisko wykonawcze nie powiedzie się powiązać do zestawu według nazwy. Na przykład, następujące metody podczas wywoływania z kodu użytkownika może spowodować, że <xref:System.AppDomain.AssemblyResolve> zdarzenia:  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, którego pierwszy argument jest ciąg reprezentujący nazwę wyświetlaną zestawu do załadowania (czyli ciągu zwracanego przez <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości).  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, którego pierwszy argument jest <xref:System.Reflection.AssemblyName> obiektu, który identyfikuje zestawu do załadowania.  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Przeciążenie metody.  
  
-   <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> Lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> przeciążenia metody, która tworzy wystąpienie obiektu w innej domenie aplikacji.  
  
### <a name="what-the-event-handler-does"></a>Jak działa program obsługi zdarzeń  
 Obsługa <xref:System.AppDomain.AssemblyResolve> zdarzenie otrzymuje nazwę wyświetlaną w zestawie, który ma zostać załadowany w <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> właściwości. Jeśli program obsługi nie może rozpoznać nazwę zestawu, zwraca wartość null (`Nothing` w języku Visual Basic `nullptr` w programie Visual C++).  
  
 Program obsługi, jeśli rozpoznaje nazwy zestawu może załadować i zwraca zestaw, który spełnia żądanie. Na poniższej liście opisano kilka przykładowych scenariuszy.  
  
-   Jeśli program obsługi zna lokalizację wersji zestawu, można załadować zestawu przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metodę i może zwrócić załadowany zestaw, jeśli to się powiedzie.  
  
-   Jeśli program obsługi ma dostęp do bazy danych przechowywane jako tablice typu byte zestawów, można załadować tablicy bajtów przy użyciu jednej z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, przyjmujące tablicy bajtów.  
  
-   Program obsługi, można wygenerować zestawu dynamicznego i przywrócić go.  
  
> [!NOTE]
>  Program obsługi musi załadować zestawu do obciążenia z kontekstu, w kontekście ładowania lub bez kontekstu. Jeśli program obsługi ładuje zestawu do kontekstu reflection-only przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> próba obciążenia metody, która wywołała <xref:System.AppDomain.AssemblyResolve> zakończy się niepowodzeniem.  
  
 Jest odpowiedzialny za program obsługi zdarzeń, aby powrócić do odpowiedniego zestawu. Program obsługi może przeanalizować nazwę wyświetlaną żądany zestaw, przekazując <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> wartość właściwości <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktora. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć programu obsługi <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwości w celu określenia, czy bieżące żądanie dotyczy zależność innego zestawu. Te informacje mogą pomóc w identyfikacji zestawu, który będzie odpowiadał zależności.  
  
 Program obsługi zdarzeń może zwrócić inną wersję zestawu niż wersja, której zażądano.  
  
 W większości przypadków zestawu, który jest zwracany przez program obsługi pojawia się w kontekście ładowania, niezależnie od kontekstu, którego program obsługi ładuje je do. Na przykład, jeśli program obsługi używa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodę, aby załadować zestawu do kontekstu ładowania z zestawu jest wyświetlany w kontekście ładowania, gdy program obsługi zwraca go. Jednak w przypadku następujących zestawu pojawia się bez kontekście podczas obsługi zwraca go:  
  
-   Program obsługi ładuje zestaw bez kontekstu.  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Właściwość nie ma wartości null.  
  
-   Żądanie zestawu (czyli zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwość) została załadowana bez kontekstu.  
  
 Aby uzyskać informacje o kontekstach, zobacz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> przeciążenie metody.  
  
 Wiele wersji tego samego zestawu mogą zostać załadowane do tej samej domenie aplikacji. Taka praktyka nie jest zalecane, ponieważ może to prowadzić do typu przydziału problemów. Zobacz [najlepsze rozwiązania dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Czego nie powinien wykonać program obsługi zdarzeń  
 Podstawowe reguły obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenie jest, że nie powinien próbuj zwrócić zestawu nie rozpoznają. Podczas pisania programu obsługi, należy wiedzieć, zestawy, które mogą spowodować, że zdarzenia do wywołania. Twoja procedura obsługi powinna zwracać wartość null dla innych zestawów.  
  
> [!IMPORTANT]
>  Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> zdarzenie jest wywoływane dla zestawów satelickich. Ta zmiana ma wpływ na program obsługi zdarzeń, który został napisany dla starszej wersji programu .NET Framework, jeśli program obsługi próbuje rozpoznać wszystkie żądania ładowania zestawu. Ta zmiana nie dotyczy programów obsługi zdarzeń, które Ignoruj zestawy, które nie rozpoznają: Zwracają wartość null, a po nim normalne mechanizmy rezerwowego.  
  
 Podczas ładowania zestawu, program obsługi zdarzeń nie mogą używać dowolnego z <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, które mogą powodować <xref:System.AppDomain.AssemblyResolve> zdarzenia można podniesione cyklicznie, ponieważ może to prowadzić do przepełnienia stosu. (Zobacz listę podane wcześniej w tym temacie). Dzieje się tak nawet wtedy, gdy zapewniają obsługę dla żądania załadowania wyjątków, ponieważ jest zgłaszany żaden wyjątek, dopóki nie zwrócono wszystkich procedur obsługi zdarzeń. W związku z tym, poniższy kod powoduje przepełnienie stosu Jeśli `MyAssembly` nie można odnaleźć:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Używanie domeny aplikacji](../../../docs/framework/app-domains/use.md)
