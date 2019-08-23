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
ms.openlocfilehash: 3844f3f1f4135167ac5575dafb4ba63a19b8b55e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927916"
---
# <a name="resolving-assembly-loads"></a>Rozwiązywanie załadowań zestawów
.NET Framework zawiera <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie dla aplikacji, które wymagają większej kontroli nad ładowaniem zestawu. Dzięki obsłudze tego zdarzenia aplikacja może załadować zestaw do kontekstu obciążenia spoza normalnej ścieżki sondowania, wybrać kilka wersji zestawu do załadowania, emitować zestaw dynamiczny i zwrócić go i tak dalej. Ten temat zawiera wskazówki dotyczące obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenia.  
  
> [!NOTE]
> W celu rozpoznawania obciążeń zestawów w kontekście tylko odbicia należy zamiast tego użyć <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> zdarzenia.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak działa zdarzenie AssemblyResolve  
 Po zarejestrowaniu procedury obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzenia program obsługi jest wywoływany za każdym razem, gdy środowisko uruchomieniowe nie zostanie powiązane z zestawem według nazwy. Na przykład wywoływanie następujących metod z kodu użytkownika może spowodować <xref:System.AppDomain.AssemblyResolve> podniesienie poziomu zdarzenia:  
  
- Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Przeciążenie metody, których pierwszy argument jest ciągiem, który reprezentuje nazwę wyświetlaną zestawu do załadowania (czyli ciąg zwracany przez <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> Właściwość). <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Przeciążenie metody, <xref:System.Reflection.AssemblyName> których pierwszy argument jest obiektem, który identyfikuje zestaw do załadowania. <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- Przeciążenie <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.  
  
- Przeciążenie metody <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> lub, które tworzy wystąpienie obiektu w innej domenie aplikacji. <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType>  
  
### <a name="what-the-event-handler-does"></a>Działanie programu obsługi zdarzeń  
 Procedura obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzenia otrzymuje nazwę wyświetlaną zestawu, który ma zostać załadowany <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> we właściwości. Jeśli program obsługi nie rozpoznaje nazwy zestawu, zwraca wartość null (`Nothing` w Visual Basic, `nullptr` w wizualizacji C++).  
  
 Jeśli program obsługi rozpoznaje nazwę zestawu, może ładować i zwracać zestaw, który spełnia żądanie. Na poniższej liście opisano kilka przykładowych scenariuszy.  
  
- Jeśli program obsługi wie lokalizację wersji zestawu, może załadować zestaw za pomocą <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody lub <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> i może zwrócić załadowany zestaw, jeśli zakończono pomyślnie.  
  
- Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywanych jako tablice bajtowe, może załadować tablicę bajtową przy użyciu jednego z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążeń metody przyjmujących tablicę bajtów.  
  
- Program obsługi może wygenerować zestaw dynamiczny i zwrócić go.  
  
> [!NOTE]
> Program obsługi musi załadować zestaw do kontekstu ładowania z w kontekście ładowania lub bez kontekstu. Jeśli program obsługi ładuje zestaw do kontekstu "tylko odbicie" przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> metody lub, próba <xref:System.AppDomain.AssemblyResolve> załadowania, która wywołała zdarzenie, kończy się niepowodzeniem.  
  
 Do zwrócenia odpowiedniego zestawu jest odpowiedzialna procedura obsługi zdarzeń. Program obsługi może przeanalizować nazwę wyświetlaną żądanego zestawu, przekazując <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> wartość właściwości <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> do konstruktora. Począwszy od .NET Framework 4, program obsługi może użyć właściwości, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> aby określić, czy bieżące żądanie jest zależne od innego zestawu. Te informacje mogą ułatwić zidentyfikowanie zestawu, który będzie spełniał zależność.  
  
 Program obsługi zdarzeń może zwrócić inną wersję zestawu niż żądana wersja.  
  
 W większości przypadków zestaw, który jest zwracany przez program obsługi, pojawia się w kontekście ładowania, niezależnie od kontekstu, w którym program obsługi ładuje go do. Jeśli na przykład program obsługi używa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody do załadowania zestawu do kontekstu ładowania z, zestaw pojawia się w kontekście ładowania, gdy program obsługi zwróci go. Jednak w poniższym przypadku zestaw pojawia się bez kontekstu, gdy program obsługi zwróci go:  
  
- Procedura obsługi ładuje zestaw bez kontekstu.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Właściwość nie ma wartości null.  
  
- Zestaw żądający (czyli zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Właściwość) został załadowany bez kontekstu.  
  
 Aby uzyskać informacje na temat kontekstów <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> , zobacz Przeciążenie metody.  
  
 Wiele wersji tego samego zestawu może być załadowanych do tej samej domeny aplikacji. Ta metoda nie jest zalecana, ponieważ może to prowadzić do problemów z przypisaniem. Zapoznaj się z [najlepszymi rozwiązaniami dotyczącymi ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Czego nie powinien wykonać program obsługi zdarzeń  
 Podstawową regułą obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenia jest to, że nie należy próbować zwrócić zestawu, który nie jest rozpoznawany. Podczas pisania procedury obsługi należy wiedzieć, które zestawy mogą spowodować podniesienie poziomu zdarzenia. Program obsługi powinien zwrócić wartość null dla innych zestawów.  
  
> [!IMPORTANT]
> Począwszy od .NET Framework 4, <xref:System.AppDomain.AssemblyResolve> zdarzenie jest zgłaszane dla zestawów satelickich. Ta zmiana ma wpływ na procedurę obsługi zdarzeń, która została zapisywana dla starszej wersji .NET Framework, jeśli program obsługi podejmie próbę rozpoznania wszystkich żądań ładowania zestawu. Obsługa zdarzeń, które ignorują zestawy, które nie są rozpoznawane przez tę zmianę: Zwracają one wartość null i są przestrzegane normalne mechanizmy powrotu.  
  
 Podczas ładowania zestawu procedura obsługi zdarzeń nie może używać żadnych <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.AssemblyResolve> przeciążeń lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metod, które mogą spowodować rekursywne zdarzenie, ponieważ może to prowadzić do przepełnienia stosu. (Zobacz listę znajdującą się wcześniej w tym temacie). Dzieje się tak nawet wtedy, gdy podajesz obsługę wyjątków dla żądania ładowania, ponieważ żaden wyjątek nie jest zgłaszany do momentu zwrócenia wszystkich programów obsługi zdarzeń. W rezultacie następujący kod powoduje przepełnienie stosu, jeśli `MyAssembly` nie zostanie znaleziony:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze praktyki dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
