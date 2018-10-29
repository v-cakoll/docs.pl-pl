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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c43f75dc17d49fe34094829387673b0f1f1d028
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201585"
---
# <a name="best-practices-for-assembly-loading"></a>Najlepsze praktyki dotyczące ładowania zestawu
W tym artykule omówiono sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>i inne błędy. W tym artykule omówiono następujące zalecenia:  
  
-   [Zrozumieć zalety i wady konteksty ładowania](#load_contexts)  
  
-   [Należy unikać powiązaniu w elemencie nazwy zestawów częściowej](#avoid_partial_names)  
  
-   [Unikaj podczas ładowania zestawu w wielu kontekstach](#avoid_loading_into_multiple_contexts)  
  
-   [Unikaj podczas ładowania wielu wersji zestawu, w tym samym kontekście](#avoid_loading_multiple_versions)  
  
-   [Rozważ przejście na domyślny kontekst ładowania](#switch_to_default)  
  
 Pierwszego zalecenia [zrozumieć zalety i wady konteksty ładowania](#load_contexts), zawiera ogólne informacje dla innych zaleceń, ponieważ zależą one wszystkie znajomości konteksty ładowania.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Zrozumieć zalety i wady konteksty ładowania  
 W ramach domeny aplikacji zestawów może być załadowany do jednej z trzech kontekstów, lub może być załadowany bez kontekstu:  
  
-   Domyślny kontekst ładowania zawiera zestawy znalezione przez sondowanie global assembly cache magazynu zestawów hosta, jeśli środowisko wykonawcze jest hostowana (na przykład w programie SQL Server), a <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> domeny aplikacji. Większość przeciążenia <xref:System.Reflection.Assembly.Load%2A> metoda Ładuj zestawy w tym kontekście.  
  
-   Kontekst load-from zawiera zestawy, które są ładowane z lokalizacji, które nie są przeszukiwane przez moduł ładujący. Na przykład dodatków może być zainstalowane w katalogu, który nie znajduje się w ścieżce aplikacji. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, i <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> przedstawiono przykładowe metody, które są ładowane przy użyciu ścieżki.  
  
-   Kontekstu reflection-only zawiera zestawy, ładowane z <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody. Nie można wykonać kod w tym kontekście, więc nie jest tutaj omówiona. Aby uzyskać więcej informacji, zobacz [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Jeśli przemijający zestaw dynamiczny jest generowany przy użyciu odbicia emisji, zestaw nie jest w jakimkolwiek kontekście. Ponadto większość zestawów, które są ładowane przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A> metody zostały załadowane bez kontekstu i zestawy, które są ładowane z tablic bajtowych są załadowane bez kontekstu, chyba że tożsamości (po zastosowaniu zasad) określa, czy znajdują się w Globalna pamięć podręczna zestawów.  
  
 Kontekstów wykonanie mają zalety i wady, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="default-load-context"></a>Domyślny kontekst ładowania  
 Gdy zestawy są ładowane do domyślny kontekst ładowania, ich zależności są ładowane automatycznie. Automatycznie znaleziono zależności, które są ładowane do domyślny kontekst ładowania dla zestawów w domyślny kontekst ładowania lub kontekst load-from. Ładowanie przez tożsamość w zestawie zwiększenie stabilności aplikacji, zapewniając, że nieznane wersje zestawów nie są używane (zobacz [uniknąć powiązanie dla nazwy zestawów częściowej](#avoid_partial_names) sekcji).  
  
 Używając domyślnego kontekstu obciążenia ma następujące wady:  
  
-   Zależności, które są ładowane do innych kontekstach nie są dostępne.  
  
-   Nie można załadować zestawów z lokalizacji poza ścieżką badania do domyślny kontekst ładowania.  
  
### <a name="load-from-context"></a>Kontekst Load-From  
 Kontekst load-from umożliwia Ładuj zestaw ze ścieżki, nie znajduje się w ścieżce aplikacji, a w związku z tym nie są objęte sondowania. Umożliwia ona zależności zlokalizowanie i ładowane z tej ścieżki, ponieważ informacje o ścieżce są obsługiwane przez kontekst. Ponadto zestawów w tym kontekście użyć zależności, które są ładowane do domyślny kontekst ładowania.  
  
 Ładowanie zestawów przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody lub jednej z metod, które są ładowane przy użyciu ścieżki, ma następujące wady:  
  
-   Jeśli zestaw o tej samej tożsamości jest już załadowany, <xref:System.Reflection.Assembly.LoadFrom%2A> zwraca załadowany zestaw, nawet jeśli określono inną ścieżkę.  
  
-   Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>, a później próbuje załadować tego samego zestawu według nazwy wyświetlanej zestawu w domyślnym kontekście ładowania, próba załadowania kończy się niepowodzeniem. Taka sytuacja może wystąpić, gdy zestaw jest przeprowadzona.  
  
-   Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>, i badania ścieżka zawiera zestaw o tej samej tożsamości, ale w innej lokalizacji, <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, lub inne nieoczekiwane zachowania mogą wystąpić.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> żądania <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> i <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, lub <xref:System.Net.WebPermission>, w określonej ścieżce.  
  
-   Jeśli istnieje obraz natywny dla zestawu, nie jest używany.  
  
-   Nie można załadować zestawów jako neutralnych dla domen.  
  
-   Zasady nie są stosowane w wersjach programu .NET Framework 1.0 i 1.1.  
  
### <a name="no-context"></a>Brak kontekstu  
 Trwa ładowanie bez kontekstu jest jedyną opcją dla zestawów przejściowe, które są generowane przy użyciu odbicia emisji. Trwa ładowanie bez kontekstu jest jedynym sposobem, aby załadować wiele zestawów, które mają taką samą tożsamość w jednej aplikacji domeny. Koszt badania jest unikane.  
  
 Zestawy, które są ładowane z tablic bajtowych są załadowane bez kontekstu, chyba że tożsamość zestawu, która jest ustanawiane, jeśli zasady są stosowane, jest zgodne z tożsamością zestawu w globalnej pamięci podręcznej; w takim przypadku zestaw jest ładowany z pamięci podręcznej zestawów globalnych.  
  
 Ładowanie zestawów bez kontekstu ma następujące wady:  
  
-   Inne zestawy nie można powiązać zestawy, które zostały załadowane bez kontekstu, o ile nie można obsłużyć <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
-   Zależności nie są ładowane automatycznie. Wstępne ładowanie je bez kontekstu, wstępnego ładowania ich do domyślny kontekst ładowania lub załadować je obsługi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
-   Wiele zestawów o tej samej tożsamości bez kontekstu ładowania może powodować problemy tożsamości typu jest podobne do tych spowodowane ładowania zestawów z tą samą tożsamością w wielu kontekstach. Zobacz [uniknąć wczytywania zestawu w wielu kontekstach](#avoid_loading_into_multiple_contexts).  
  
-   Jeśli istnieje obraz natywny dla zestawu, nie jest używany.  
  
-   Nie można załadować zestawów jako neutralnych dla domen.  
  
-   Zasady nie są stosowane w wersjach programu .NET Framework 1.0 i 1.1.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Należy unikać powiązanie dla nazwy zestawów częściowej  
 Powiązania nazwy częściowej występuje po określeniu tylko część nazwy wyświetlanej zestawu (<xref:System.Reflection.Assembly.FullName%2A>) podczas ładowania zestawu. Na przykład może wywołać <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody z prostą nazwę zestawu, pomijając wersji, kulturę i token klucza publicznego. Lub może wywołać <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody, który po raz pierwszy wywołuje <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodę w przypadku niepowodzenia można zlokalizować zestawu wyszukiwania w globalnej pamięci podręcznej i ładuje najnowszej dostępnej wersji zestawu.  
  
 Powiązania nazwy częściowej może spowodować wiele problemów, w tym następujące:  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Metoda może załadować innego zestawu o tej samej prostej nazwie. Na przykład dwóch aplikacji może zainstalować dwie całkowicie różne zestawy czy obie pozycje mają prostą nazwę `GraphicsLibrary` w globalnej pamięci podręcznej.  
  
-   Zestaw, który jest ładowany w rzeczywistości może nie być zgodne z poprzednimi wersjami. Na przykład nie został podany w wersji może spowodować załadowanie dużej ilości wersją nowszą niż wersja programu został początkowo zapisywane do użycia. Zmiany w nowszej wersji może spowodować błędy w aplikacji.  
  
-   Zestaw, który jest ładowany w rzeczywistości może nie być zgodne. Na przykład możesz może mieć tworzone i testowane na aplikację do najnowszej wersji zestawu, ale powiązanie częściowe może ładować znacznie starszą wersję, która nie ma funkcji używanych przez aplikację.  
  
-   Instalowanie nowych aplikacji może uszkodzić istniejące aplikacje. Aplikacja, która używa <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda można zaburzyć przez zainstalowanie nowszej, niezgodnej wersji zestaw współużytkowany.  
  
-   Mogą wystąpić nieoczekiwane zależności ładowania. Załadować dwa zestawy tego udziału, zależności, ładowania ich z powiązaniem częściowe mogą wystąpić w jednym zestawie za pomocą składnika, który nie był skompilowany lub przetestowane za pomocą.  
  
 Z powodu problemów, może to spowodować <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda ma został oznaczony jako przestarzały. Firma Microsoft zaleca użycie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody zamiast tego i określić pełny zestaw nazw wyświetlanych. Zobacz [zrozumieć zalety i wady konteksty ładowania](#load_contexts) i [rozważ przejście na domyślny kontekst ładowania](#switch_to_default).  
  
 Jeśli chcesz używać <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metody ponieważ wprowadza łatwe w użyciu z ładowaniem zestawu, należy wziąć pod uwagę że zakończyć się niepowodzeniem z komunikatem o błędzie, który identyfikuje brakujący zestaw aplikacji jest prawdopodobne zapewnić lepsze środowisko użytkownika niż automatycznie przy użyciu Nieznana wersja zestawu, która może spowodować nieprzewidywalne zachowanie i zabezpieczeń luki.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Unikaj podczas ładowania zestawu w wielu kontekstach  
 Podczas ładowania zestawu w wielu kontekstach może powodować problemy tożsamości typu. Jeśli ten sam typ jest ładowany z tego samego zestawu w dwóch różnych kontekstach, jest tak, jakby został załadowany dwa różne typy o takiej samej nazwie. <xref:System.InvalidCastException> Jest generowany, jeśli zostanie podjęta próba rzutowania typu do drugiej z mylące komunikat, który typ `MyType` nie można rzutować na typ `MyType`.  
  
 Na przykład załóżmy, że `ICommunicate` interfejs jest zadeklarowany w zestawie o nazwie `Utility`, który jest przywoływany przez program, a także innych zestawów, które ładuje programu. Zestawy te zawierają typy implementujące `ICommunicate` interfejsu, dzięki czemu program, aby ich używać.  
  
 Teraz należy rozważyć, co się stanie po uruchomieniu programu. Zestawy, które są przywoływane przez Twój program jest ładowana do domyślny kontekst ładowania. Jeśli załadujesz zestawu docelowego przez swoją tożsamość za pomocą <xref:System.Reflection.Assembly.Load%2A> metody będzie domyślny kontekst ładowania i dlatego będzie jego zależności. Zarówno program, jak i zestaw docelowy będzie używać tego samego `Utility` zestawu.  
  
 Jednak Załóżmy, że ładowanie zestawu docelowego przy użyciu ścieżki pliku przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A> metody. Zestaw jest ładowany bez żadnego kontekstu, dzięki czemu jego zależności nie są ładowane automatycznie. Może mieć program obsługi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby podać zależność która może ładować `Utility` zestawu za pomocą kontekstu przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A> metody. Teraz podczas tworzenia wystąpienia typu, który jest zawarty w zestawie docelowym i spróbuj przypisać ją do zmiennej typu `ICommunicate`, <xref:System.InvalidCastException> jest generowany, ponieważ środowisko uruchomieniowe uwzględnia `ICommunicate` interfejsy w dwie kopie `Utility` zestawu do różnych typów.  
  
 Istnieje wiele innych scenariuszach, w których zespół może być załadowany do wielu kontekstach. Najlepszym rozwiązaniem jest, aby uniknąć konfliktów przemieszczanie zestawu docelowego w ścieżce aplikacji i rozpoczęcie używania <xref:System.Reflection.Assembly.Load%2A> metody z Pełna nazwa wyświetlana. Zestaw jest następnie ładowany domyślny kontekst ładowania, a oba zestawy używać tego samego `Utility` zestawu.  
  
 Jeśli zestaw docelowy musi pozostać poza ścieżki aplikacji, możesz użyć <xref:System.Reflection.Assembly.LoadFrom%2A> metodę, aby załadować je do kontekst load-from. Jeśli zestaw docelowy został skompilowany z odwołaniem do swojej aplikacji `Utility` zestawu, będzie używać `Utility` zestawu, który aplikacji został załadowany do domyślny kontekst ładowania. Należy pamiętać, że mogą wystąpić problemy, jeśli zestaw docelowy ma zależność od kopię `Utility` zestawu znajdujących się poza ścieżki aplikacji. Jeśli ten zestaw jest ładowany do kontekst load-from przed ładowanie aplikacji `Utility` zestawu, ładowania aplikacji zakończy się niepowodzeniem.  
  
 [Rozważ przełączenie do kontekstu ładowania domyślne](#switch_to_default) sekcji omówiono alternatywy dla przy użyciu ładowania ścieżki plików, takich jak <xref:System.Reflection.Assembly.LoadFile%2A> i <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Unikaj podczas ładowania wielu wersji zestawu, w tym samym kontekście  
 Ładowanie wielu wersji zestawu do kontekstu ładowania co może powodować problemy tożsamości typu. Jeśli ten sam typ jest ładowany z dwóch wersji tego samego zestawu, jest tak, jakby został załadowany dwa różne typy o takiej samej nazwie. <xref:System.InvalidCastException> Jest generowany, jeśli zostanie podjęta próba rzutowania typu do drugiej z mylące komunikat, który typ `MyType` nie można rzutować na typ `MyType`.  
  
 Na przykład program może załadować jednej wersji `Utility` zestawu bezpośrednio, a później go może załadować innego zestawu, który ładuje różne wersje programu `Utility` zestawu. Lub błędu w kodzie może spowodować, że dwa różne ścieżki w aplikacji, aby załadować różnych wersji zestawu.  
  
 W domyślnym kontekście ładowania, ten problem może wystąpić, gdy używasz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodę i określić kompletny zestaw wyświetlane nazwy, które obejmują różnych numerów wersji. Dla zestawów, które zostały załadowane bez kontekstu, problem może być spowodowany przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metodę, aby załadować ten sam zestaw z różnych ścieżek. Środowisko uruchomieniowe uwzględnia dwa zestawy, które są ładowane z różnych ścieżek za różne zestawy, nawet jeśli ich tożsamości są takie same.  
  
 Oprócz typu tożsamości problemy, może spowodować wielu wersji zestawu <xref:System.MissingMethodException> Jeśli typ, który jest ładowany z jednej wersji zestawu jest przekazywany do kodu, który oczekuje, że tego typu z innej wersji. Na przykład kod może oczekiwać metodę, która została dodana do nowszej wersji.  
  
 Bardziej subtelne błędów może wystąpić, jeśli zachowanie tego typu zmieniony między wersjami. Na przykład metoda może zgłosić nieoczekiwany wyjątek lub zwrócić nieoczekiwaną wartość.  
  
 Należy dokładnie przejrzeć swój kod, aby upewnić się, że tylko jeden załadowaniu wersją zestawu. Możesz użyć <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> metodę, aby określić zestawy, które są ładowane w danym momencie.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Rozważ przejście na domyślny kontekst ładowania  
 Sprawdź wzorców ładowania i wdrożenia zestawu aplikacji. Możesz wyeliminować zestawów, które są ładowane z tablic bajtowych Czy jest możliwe przeniesienie zestawów w ścieżce badania? Jeśli zestawy znajdują się w globalnej pamięci podręcznej lub w domenie aplikacji przez sondowanie ścieżki (oznacza to, że jego <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A>), można załadować zestawu, jego tożsamość.  
  
 Jeśli nie jest możliwe umieszczenie wszystkich zestawów w ścieżce badania, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak za pomocą model dodatku .NET Framework, umieszczenie zestawów w globalnej pamięci podręcznej lub tworzenia domen aplikacji.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Należy wziąć pod uwagę przy użyciu platformy .NET Framework Model dodatku  
 Jeśli używasz kontekst load-from można zaimplementować dodatki, które zwykle nie są zainstalowane w bazie danych aplikacji, należy użyć model dodatku .NET Framework. Ten model zawiera izolacja na poziomie domeny lub procesu aplikacji, bez konieczności zarządzania domenami aplikacji, samodzielnie. Aby uzyskać informacje na temat modelu dodatku, zobacz [dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Należy rozważyć użycie Global Assembly Cache  
 Miejsce zestawów w globalnej pamięci podręcznej, aby skorzystać z zalet ścieżka udostępnionego zestawu jest poza aplikacją podstawowej, bez utraty korzyści wynikające z domyślny kontekst ładowania lub tworzenia wady innych kontekstach.  
  
### <a name="consider-using-application-domains"></a>Należy rozważyć używanie domen aplikacji  
 Jeśli okaże się, że niektóre zestawy nie można wdrożyć w ścieżce badania aplikacji, należy rozważyć utworzenie nowej domeny aplikacji dla tych zestawów. Użyj <xref:System.AppDomainSetup> tworzenia nowej domeny aplikacji i używania <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> właściwości w celu określenia ścieżki, zawierającego zestawy do załadowania. Jeśli masz wiele katalogów sondowania, można ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> katalog główny i używania <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> właściwość do identyfikacji podkatalogów sondowania. Alternatywnie możesz utworzyć wiele domen aplikacji i ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> każdej domeny aplikacji odpowiednią ścieżkę na jej zestawów.  
  
 Należy zauważyć, że można użyć <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodę, aby załadować te zestawy. Ponieważ są one teraz w ścieżce badania, będą ładowane do domyślny kontekst ładowania zamiast kontekst load-from. Jednak zaleca się przejście na <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody i podaj pełny zestaw nazw wyświetlanych, aby upewnić się, że poprawne wersje są zawsze używane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
- [Dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md)
