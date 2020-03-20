---
title: Najlepsze praktyki dotyczące ładowania zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies,binding
- LoadFrom method
- default load context
- TypeLoadException class,causes
- assembly loading errors
- load contexts
- assemblies,loading
- LoadWithPartialName method
- load-from context
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
ms.openlocfilehash: 7575c40edf47e977335bcc34fcd9e49debab0980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181699"
---
# <a name="best-practices-for-assembly-loading"></a>Najlepsze praktyki dotyczące ładowania zestawu
W tym artykule omówiono sposoby uniknięcia <xref:System.InvalidCastException> <xref:System.MissingMethodException>problemów z tożsamością typu, które mogą prowadzić do , i innych błędów. W artykule omówiono następujące zalecenia:  
  
- [Zrozumienie zalet i wad kontekstów obciążenia](#load_contexts)  
  
- [Unikaj powiązania z nazwami zespołów częściowych](#avoid_partial_names)  
  
- [Unikaj ładowania złożenia do wielu kontekstów](#avoid_loading_into_multiple_contexts)  
  
- [Unikaj ładowania wielu wersji zestawu do tego samego kontekstu](#avoid_loading_multiple_versions)  
  
- [Rozważ przełączenie do domyślnego kontekstu obciążenia](#switch_to_default)  
  
 Pierwsze zalecenie, [zrozumieć zalety i wady kontekstów obciążenia](#load_contexts), zawiera podstawowe informacje dla innych zaleceń, ponieważ wszystkie one zależą od znajomości kontekstów obciążenia.  
  
<a name="load_contexts"></a>
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Zrozumienie zalet i wad kontekstów obciążenia  
 W domenie aplikacji zestawy mogą być ładowane do jednego z trzech kontekstów lub mogą być ładowane bez kontekstu:  
  
- Domyślny kontekst ładowania zawiera zestawy znalezione przez sondowanie globalnej pamięci podręcznej zestawów, magazynu zestawu hosta, <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> jeśli środowisko uruchomieniowe jest hostowane (na przykład w programie SQL Server) oraz domeny aplikacji. Większość przeciążeń <xref:System.Reflection.Assembly.Load%2A> zestawów obciążenia metody w tym kontekście.  
  
- Kontekst ładowania z zawiera zestawy, które są ładowane z lokalizacji, które nie są przeszukiwane przez moduł ładujący. Na przykład dodatki mogą być instalowane w katalogu, który nie znajduje się pod ścieżką aplikacji. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>i <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> są przykładami metod, które ładują się według ścieżki.  
  
- Kontekst tylko do odbicia zawiera zestawy <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> ładowane z i metody. Nie można wykonać kodu w tym kontekście, więc nie jest on omawiany w tym miejscu. Aby uzyskać więcej informacji, zobacz [Jak: Ładowanie zestawów do kontekstu tylko do odbicia](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Jeśli wygenerowano przejściowy zestaw dynamiczny przy użyciu odbicia emitować, zestaw nie jest w żadnym kontekście. Ponadto większość zestawów, które są <xref:System.Reflection.Assembly.LoadFile%2A> ładowane przy użyciu metody są ładowane bez kontekstu i zestawy, które są ładowane z tablic bajtowych są ładowane bez kontekstu, chyba że ich tożsamość (po zastosowaniu zasad) ustanawia, że są one w globalnej pamięci podręcznej zestawów.  
  
 Konteksty wykonywania mają zalety i wady, jak omówiono w poniższych sekcjach.  
  
### <a name="default-load-context"></a>Domyślny kontekst ładowania  
 Gdy zestawy są ładowane do domyślnego kontekstu obciążenia, ich zależności są ładowane automatycznie. Zależności, które są ładowane do domyślnego kontekstu obciążenia znajdują się automatycznie dla zestawów w kontekście ładowania domyślnego lub kontekstu ładowania z. Ładowanie przez tożsamość zestawu zwiększa stabilność aplikacji, zapewniając, że nieznane wersje zestawów nie są używane (zobacz [Avoid powiązania na częściowe nazwy zestawu](#avoid_partial_names) sekcji).  
  
 Przy użyciu domyślnego kontekstu obciążenia ma następujące wady:  
  
- Zależności, które są ładowane do innych kontekstów nie są dostępne.  
  
- Nie można załadować zestawów z lokalizacji poza ścieżką sondowania do domyślnego kontekstu obciążenia.  
  
### <a name="load-from-context"></a>Kontekst ładowania z  
 Kontekst ładowania z umożliwia załadowanie złożenia ze ścieżki, która nie znajduje się pod ścieżką aplikacji i dlatego nie jest uwzględniona w sondowaniu. Umożliwia zależności do zlokalizowania i załadowania z tej ścieżki, ponieważ informacje o ścieżce jest obsługiwany przez kontekst. Ponadto zestawy w tym kontekście można użyć zależności, które są ładowane do domyślnego kontekstu obciążenia.  
  
 Ładowanie zestawów przy <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> użyciu metody lub jednej z innych metod, które ładują się według ścieżki, ma następujące wady:  
  
- Jeśli zestaw o tej samej <xref:System.Reflection.Assembly.LoadFrom%2A> tożsamości jest już załadowany, zwraca załadowany zestaw, nawet jeśli określono inną ścieżkę.  
  
- Jeśli zestaw jest <xref:System.Reflection.Assembly.LoadFrom%2A>ładowany z , a później zestaw w kontekście obciążenia domyślnego próbuje załadować ten sam zestaw według nazwy wyświetlanej, próba obciążenia kończy się niepowodzeniem. Może to nastąpić, gdy zestaw jest deserialized.  
  
- Jeśli zestaw jest <xref:System.Reflection.Assembly.LoadFrom%2A>ładowany z , a ścieżka sondowania zawiera zestaw o <xref:System.InvalidCastException> <xref:System.MissingMethodException>tej samej tożsamości, ale w innej lokalizacji, może wystąpić , lub inne nieoczekiwane zachowanie.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A><xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> i <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, lub <xref:System.Net.WebPermission>, na określonej ścieżce.  
  
- Jeśli natywny obraz istnieje dla zestawu, nie jest używany.  
  
- Zestawu nie można załadować jako neutralne domeny.  
  
- W .NET Framework w wersjach 1.0 i 1.1 zasady nie są stosowane.  
  
### <a name="no-context"></a>Brak kontekstu  
 Ładowanie bez kontekstu jest jedyną opcją dla zespołów przejściowych, które są generowane za pomocą emitowania odbicia. Ładowanie bez kontekstu jest jedynym sposobem, aby załadować wiele zestawów, które mają tę samą tożsamość w jednej domenie aplikacji. Unika się kosztów sondowania.  
  
 Zestawy, które są ładowane z tablic bajtów są ładowane bez kontekstu, chyba że tożsamość zestawu, który jest ustanawiany po zastosowaniu zasad, pasuje do tożsamości zestawu w globalnej pamięci podręcznej zestawów; w takim przypadku zestaw jest ładowany z globalnej pamięci podręcznej zestawów.  
  
 Ładowanie zestawów bez kontekstu ma następujące wady:  
  
- Inne zestawy nie można powiązać z zestawami, które <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> są ładowane bez kontekstu, chyba że obsługujesz zdarzenie.  
  
- Zależności nie są ładowane automatycznie. Można wstępnie załadować je bez kontekstu, wstępnie załadować je do <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> domyślnego kontekstu obciążenia lub załadować je przez obsługę zdarzenia.  
  
- Ładowanie wielu zestawów o tej samej tożsamości bez kontekstu może spowodować problemy tożsamości typu podobne do tych spowodowanych przez ładowanie zestawów o tej samej tożsamości w wielu kontekstach. Zobacz [Unikanie ładowania zestawu do wielu kontekstów](#avoid_loading_into_multiple_contexts).  
  
- Jeśli natywny obraz istnieje dla zestawu, nie jest używany.  
  
- Zestawu nie można załadować jako neutralne domeny.  
  
- W .NET Framework w wersjach 1.0 i 1.1 zasady nie są stosowane.  
  
<a name="avoid_partial_names"></a>
## <a name="avoid-binding-on-partial-assembly-names"></a>Unikanie powiązania nazw zespołów częściowych  
 Częściowe powiązanie nazwy występuje po określeniu<xref:System.Reflection.Assembly.FullName%2A>tylko części nazwy wyświetlanej złożenia ( ) podczas ładowania złożenia. Na przykład można wywołać <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodę tylko z prostą nazwą zestawu, pomijając wersję, kultury i tokenu klucza publicznego. Lub można wywołać <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metodę, która <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> najpierw wywołuje metodę i, jeśli nie można zlokalizować zestawu, przeszukuje globalną pamięć podręczną zestawu i ładuje najnowszą dostępną wersję zestawu.  
  
 Częściowe powiązanie nazwy może powodować wiele problemów, w tym następujące:  
  
- Metoda <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> może załadować inny zestaw o tej samej prostej nazwie. Na przykład dwie aplikacje mogą zainstalować dwa zupełnie różne `GraphicsLibrary` zestawy, które obie mają prostą nazwę w globalnej pamięci podręcznej zestawów.  
  
- Zestaw, który jest faktycznie załadowany może nie być wstecznie kompatybilny. Na przykład nie określenie wersji może spowodować załadowanie znacznie nowszej wersji niż wersja, której program został pierwotnie napisany do użycia. Zmiany w nowszej wersji mogą powodować błędy w aplikacji.  
  
- Zestaw, który jest faktycznie załadowany może nie być zgodny z przodu. Na przykład być może zostały smątą i przetestowaną aplikacją przy użyciu najnowszej wersji zestawu, ale częściowe powiązanie może załadować znacznie wcześniejszą wersję, która nie ma funkcji używanych przez aplikację.  
  
- Instalowanie nowych aplikacji może przerwać istniejące aplikacje. Aplikacja, która używa <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metody można podzielić, instalując nowszą, niezgodną wersję zestawu udostępnionego.  
  
- Może wystąpić nieoczekiwane ładowanie zależności. To załadować dwa zestawy, które współużytkują zależność, ładowanie ich z częściowego powiązania może spowodować jeden zestaw przy użyciu składnika, który nie został zbudowany lub przetestowane z.  
  
 Ze względu na problemy, <xref:System.Reflection.Assembly.LoadWithPartialName%2A> które może spowodować, metoda została oznaczona jako przestarzałe. Zaleca się użycie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody zamiast i określić pełne nazwy wyświetlane zestawu. Zobacz [Opis zalet i wad kontekstów obciążenia](#load_contexts) i rozważ [przełączenie do kontekstu obciążenia domyślnego](#switch_to_default).  
  
 Jeśli chcesz użyć <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metody, ponieważ ułatwia ładowanie zestawu, należy wziąć pod uwagę, że o aplikacji nie powiedzie się z komunikatem o błędzie, który identyfikuje brakujący zestaw może zapewnić lepsze środowisko użytkownika niż automatycznie przy użyciu nieznanej wersji zestawu, co może spowodować nieprzewidywalne zachowanie i luki w zabezpieczeniach.  
  
<a name="avoid_loading_into_multiple_contexts"></a>
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Unikaj ładowania zestawu do wielu kontekstów  
 Ładowanie zestawu do wielu kontekstów może spowodować problemy z tożsamością typu. Jeśli ten sam typ jest ładowany z tego samego zestawu do dwóch różnych kontekstów, to tak, jakby dwa różne typy o tej samej nazwie zostały załadowane. Jest <xref:System.InvalidCastException> generowany, jeśli spróbujesz rzutować jeden typ do `MyType` drugiego, z `MyType`mylącą wiadomością, że typ nie może być rzutowania do typu .  
  
 Załóżmy na `ICommunicate` przykład, że interfejs `Utility`jest zadeklarowany w zestawie o nazwie , do którego odwołuje się program, a także inne zestawy, które program ładuje. Te inne zestawy zawierają typy, które implementują `ICommunicate` interfejs, dzięki czemu program z nich korzystać.  
  
 Teraz zastanów się, co się stanie, gdy program jest uruchamiany. Zestawy, do których odwołuje się program, są ładowane do domyślnego kontekstu obciążenia. Jeśli załadować zestaw docelowy przez <xref:System.Reflection.Assembly.Load%2A> jego tożsamości, przy użyciu metody, będzie w kontekście obciążenia domyślnego i tak będzie jego zależności. Zarówno program, jak i zestaw `Utility` docelowy będą używać tego samego zestawu.  
  
 Załóżmy jednak, że zestaw docelowy jest <xref:System.Reflection.Assembly.LoadFile%2A> ładowany przez jego ścieżkę pliku, przy użyciu metody. Zestaw jest ładowany bez kontekstu, więc jego zależności nie są automatycznie ładowane. Może mieć program obsługi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> dla zdarzenia do dostarczania zależności i `Utility` może załadować zestaw <xref:System.Reflection.Assembly.LoadFile%2A> bez kontekstu przy użyciu metody. Teraz podczas tworzenia wystąpienia typu, który jest zawarty w zestawie docelowym i spróbuj `ICommunicate`przypisać <xref:System.InvalidCastException> go do zmiennej typu, jest generowany, ponieważ środowisko uruchomieniowe uważa `ICommunicate` interfejsy w dwóch kopiach `Utility` zestawu za różne typy.  
  
 Istnieje wiele innych scenariuszy, w których zestaw można załadować do wielu kontekstów. Najlepszym rozwiązaniem jest uniknięcie konfliktów przez przeniesienie zestawu docelowego <xref:System.Reflection.Assembly.Load%2A> w ścieżce aplikacji i przy użyciu metody z pełną nazwą wyświetlaną. Zestaw jest następnie ładowany do domyślnego kontekstu `Utility` obciążenia, a oba zestawy używają tego samego zestawu.  
  
 Jeśli zestaw docelowy musi pozostać poza ścieżką <xref:System.Reflection.Assembly.LoadFrom%2A> aplikacji, można użyć metody, aby załadować go do kontekstu ładowania z. Jeśli zestaw docelowy został skompilowany z `Utility` odwołaniem do `Utility` zestawu aplikacji, użyje zestawu, który aplikacja załadowała do domyślnego kontekstu obciążenia. Należy zauważyć, że mogą wystąpić problemy, jeśli zestaw `Utility` docelowy ma zależność od kopii zestawu znajdującego się poza ścieżką aplikacji. Jeśli ten zestaw jest ładowany do kontekstu `Utility` obciążenia z przed aplikacją ładuje zestawu, obciążenie aplikacji zakończy się niepowodzeniem.  
  
 Sekcja [Rozważ przełączenie do kontekstu ładowania domyślnego](#switch_to_default) omówiono alternatywy dla używania obciążeń ścieżki pliku, takich jak <xref:System.Reflection.Assembly.LoadFile%2A> i <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Unikaj ładowania wielu wersji zestawu w tym samym kontekście  
 Ładowanie wielu wersji zestawu w jednym kontekście obciążenia może spowodować problemy z tożsamością typu. Jeśli ten sam typ jest ładowany z dwóch wersji tego samego zestawu, jest tak, jakby dwa różne typy o tej samej nazwie zostały załadowane. Jest <xref:System.InvalidCastException> generowany, jeśli spróbujesz rzutować jeden typ do `MyType` drugiego, z `MyType`mylącą wiadomością, że typ nie może być rzutowania do typu .  
  
 Na przykład program może załadować `Utility` jedną wersję zestawu bezpośrednio, a później może załadować inny `Utility` zestaw, który ładuje inną wersję zestawu. Lub błąd kodowania może spowodować dwie różne ścieżki kodu w aplikacji, aby załadować różne wersje zestawu.  
  
 W kontekście ładowania domyślnego ten problem <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> może wystąpić podczas korzystania z metody i określić pełne nazwy wyświetlane zestawu, które zawierają różne numery wersji. Dla zestawów, które są ładowane bez kontekstu, problem może być spowodowane przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody, aby załadować ten sam zestaw z różnych ścieżek. Środowisko wykonawcze uważa, że dwa zestawy, które są ładowane z różnych ścieżek, są różne zestawy, nawet jeśli ich tożsamości są takie same.  
  
 Oprócz problemów z tożsamością typu wiele wersji <xref:System.MissingMethodException> zestawu może spowodować, jeśli typ, który jest ładowany z jednej wersji zestawu jest przekazywany do kodu, który oczekuje tego typu z innej wersji. Na przykład kod może oczekiwać metody, która została dodana do nowszej wersji.  
  
 Bardziej subtelne błędy mogą wystąpić, jeśli zachowanie typu zmieniono między wersjami. Na przykład metoda może zgłosić nieoczekiwany wyjątek lub zwrócić nieoczekiwaną wartość.  
  
 Dokładnie przejrzyj kod, aby upewnić się, że tylko jedna wersja zestawu jest ładowany. Za pomocą <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> tej metody można określić, które zestawy są ładowane w danym momencie.  
  
<a name="switch_to_default"></a>
## <a name="consider-switching-to-the-default-load-context"></a>Rozważ przełączenie do kontekstu obciążenia domyślnego  
 Sprawdź wzorce ładowania i wdrażania zestawu aplikacji. Czy można wyeliminować zestawy, które są ładowane z tablic bajtowych? Czy można przenieść zestawy do ścieżki sondowania? Jeśli zestawy znajdują się w globalnej pamięci podręcznej zestawów lub w <xref:System.AppDomainSetup.ApplicationBase%2A> ścieżce sondowania domeny aplikacji (czyli jej i <xref:System.AppDomainSetup.PrivateBinPath%2A>), można załadować zestaw według jego tożsamości.  
  
 Jeśli nie jest możliwe umieszczenie wszystkich zestawów w ścieżce sondowania, należy wziąć pod uwagę alternatywy, takie jak przy użyciu modelu dodatku .NET Framework, umieszczanie zestawów w globalnej pamięci podręcznej zestawów lub tworzenie domen aplikacji.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Rozważ użycie modelu dodatku .NET Framework  
 Jeśli używasz kontekstu ładowania z do zaimplementowania dodatków, które zazwyczaj nie są zainstalowane w bazie aplikacji, należy użyć modelu dodatku .NET Framework. Ten model zapewnia izolację na poziomie domeny aplikacji lub procesu, bez konieczności samodzielnego zarządzania domenami aplikacji. Aby uzyskać informacje o modelu dodatku, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Rozważ użycie globalnej pamięci podręcznej zestawów  
 Umieść zestawy w globalnej pamięci podręcznej zestawów, aby uzyskać korzyści ze ścieżki zestawu udostępnionego, która znajduje się poza bazą aplikacji, bez utraty zalet kontekstu obciążenia domyślnego lub biorąc na wady innych kontekstów.  
  
### <a name="consider-using-application-domains"></a>Rozważ użycie domen aplikacji  
 Jeśli okaże się, że niektóre zestawy nie można wdrożyć w ścieżce sondowania aplikacji, należy rozważyć utworzenie nowej domeny aplikacji dla tych zestawów. Użyj, <xref:System.AppDomainSetup> aby utworzyć nową domenę <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> aplikacji i użyj właściwości, aby określić ścieżkę zawierającą zestawy, które chcesz załadować. Jeśli masz wiele katalogów do sondowania, można ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> do <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> katalogu głównego i użyć właściwości do identyfikowania podkatalogów do sondowania. Alternatywnie można utworzyć wiele domen aplikacji <xref:System.AppDomainSetup.ApplicationBase%2A> i ustawić każdej domeny aplikacji do odpowiedniej ścieżki dla jego zestawów.  
  
 Należy zauważyć, że <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> można użyć metody, aby załadować te zestawy. Ponieważ są one teraz w ścieżce sondowania, zostaną załadowane do domyślnego kontekstu ładowania zamiast kontekstu ładowania z. Jednak zaleca się, aby <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przełączyć się do metody i podać pełne nazwy wyświetlania zestawu, aby upewnić się, że poprawne wersje są zawsze używane.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
