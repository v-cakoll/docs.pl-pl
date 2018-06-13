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
ms.openlocfilehash: b05ec604f8493ba773d9de9af19acc70c023b8bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394156"
---
# <a name="best-practices-for-assembly-loading"></a>Najlepsze praktyki dotyczące ładowania zestawu
W tym artykule opisano sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>oraz innych błędów. W tym artykule omówiono następujące zalecenia:  
  
-   [Zrozumieć zalety i wady konteksty ładowania](#load_contexts)  
  
-   [Unikaj powiązanie nazwy zestawu z częściowa](#avoid_partial_names)  
  
-   [Unikaj ładowania zestawu do wielu kontekstów](#avoid_loading_into_multiple_contexts)  
  
-   [Unikaj ładowania wielu wersji zestawu do tego samego kontekstu](#avoid_loading_multiple_versions)  
  
-   [Rozważ przejście na domyślnym kontekście ładowania](#switch_to_default)  
  
 Pierwszy zalecenie [zrozumieć zalety i wady kontekstów obciążenia](#load_contexts), przedstawiono ogólne informacje dla innych zaleceń, ponieważ wszystkie one są zależne od wiedzy kontekstów obciążenia.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Zrozumieć zalety i wady konteksty ładowania  
 W domenie aplikacji zestawy może być załadowany do jednego z trzech kontekstów lub może być załadowany bez kontekstu:  
  
-   Domyślnym kontekście ładowania zawiera zestawy znalezione przez sondowanie globalnej pamięci podręcznej zestawów, magazynie zestawów hosta, jeśli środowisko uruchomieniowe jest hostowana (na przykład w programie SQL Server) i <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> domeny aplikacji. Większość przeciążeń <xref:System.Reflection.Assembly.Load%2A> metody Ładuj zestawy w tym kontekście.  
  
-   Kontekst load-from zawiera zestawy, które są ładowane z lokalizacji, które nie są przeszukiwane przez moduł ładujący. Na przykład dodatków mogą być zainstalowane w katalogu, który nie znajduje się w ścieżce aplikacji. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, i <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> przedstawiono metody, które są ładowane przez ścieżkę.  
  
-   Kontekstu reflection-only zawiera zestawy ładowane z <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody. Kod w tym kontekście nie można wykonać, nie została omówiona w tym miejscu. Aby uzyskać więcej informacji, zobacz [porady: zestawy obciążenia w kontekście Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Jeśli zestawu przejściowego dynamicznej jest generowany przy użyciu odbicia emisji, zestaw nie znajduje się w dowolnym kontekście. Ponadto większość zestawów, które są ładowane przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A> metody zostały załadowane bez kontekstu i zestawy, które są ładowane z tablic bajtowych zostały załadowane bez kontekstu, chyba że ich tożsamość (po zastosowaniu zasad) ustanawia muszą znajdować się w Globalna pamięć podręczna zestawów.  
  
 Kontekst wykonywania ma zalety i wady, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="default-load-context"></a>Domyślnym kontekście ładowania  
 Gdy zestawy są ładowane w domyślnym kontekście ładowania, ich zależności są ładowane automatycznie. Zależności, które są ładowane w domyślnym kontekście ładowania znajdują się automatycznie dla zestawów w domyślnym kontekście ładowania lub kontekst load-from. Ładowanie przez tożsamość w zestawie zwiększenie stabilności aplikacji przez zapewnienie im nieznany wersje zestawów nie są używane (zobacz [uniknąć wiązanie częściowe nazwy zestawu](#avoid_partial_names) sekcji).  
  
 Przy użyciu domyślnym kontekście ładowania ma następujące wady:  
  
-   Zależności, które są ładowane do innych kontekstach nie są dostępne.  
  
-   Nie można załadować zestawów z lokalizacji poza ścieżki próbkowania w domyślnym kontekście ładowania.  
  
### <a name="load-from-context"></a>Kontekst Load-From  
 Kontekst load-from umożliwia załadowania zestawu z ścieżki, która nie znajduje się w ścieżce aplikacji, a zatem nie są objęte sondowanie. Umożliwia ona zależności zlokalizowanie i załadować z tej ścieżki, ponieważ informacje o ścieżce są obsługiwane przez kontekst. Ponadto zestawy, w tym kontekście użyć zależności, które są ładowane w domyślnym kontekście ładowania.  
  
 Ładowanie zestawów przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody lub jednej z metod, które są ładowane przez ścieżkę, ma następujące wady:  
  
-   Jeśli zestaw o tej samej tożsamości jest już załadowany, <xref:System.Reflection.Assembly.LoadFrom%2A> zwraca załadowany zestaw nawet wtedy, gdy określono inną ścieżkę.  
  
-   Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>i później próbuje załadować samego zestawu według nazwy wyświetlanej zestawu w domyślnym kontekście ładowania, próba załadowania kończy się niepowodzeniem. Taka sytuacja może wystąpić, gdy zestaw jest deserializacji.  
  
-   Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>, i ścieżki próbkowania zawiera zestaw o tej samej tożsamości, ale w innej lokalizacji, <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, lub mogą występować inne nieoczekiwane zachowania.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> wymagania <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> i <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, lub <xref:System.Net.WebPermission>, w określonej ścieżce.  
  
-   Jeśli zestaw obrazu macierzystego, nie jest używane.  
  
-   Nie można załadować zestawu jako neutralne dla domen.  
  
-   W wersji systemu .NET Framework 1.0 i 1.1 nie są stosowane zasady.  
  
### <a name="no-context"></a>Brak kontekstu  
 Ładowanie bez kontekstu jest jedyną opcją dla przejściowej zestawy, które są generowane z odbiciem emisji. Ładowanie bez kontekstu jest jedynym sposobem, aby załadować wielu zestawów, które mają taką samą tożsamość w domenie jedną aplikację. Unika się koszt sondowanie.  
  
 Zestawy, które są ładowane z tablic bajtowych są ładowane bez kontekstu, chyba że tożsamość zestawu, na którym jest nawiązywane po zastosowaniu zasad, odpowiada tożsamości zestawu w pamięci podręcznej GAC; w takim przypadku zestaw jest załadowany z pamięci podręcznej GAC.  
  
 Ładowanie zestawów bez kontekstu ma następujące wady:  
  
-   Inne zestawy nie można powiązać z zestawów, które zostały załadowane bez kontekstu, o ile nie można obsłużyć <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
-   Zależności nie są ładowane automatycznie. Można wstępnie je bez kontekstu, wstępnie je w domyślnym kontekście ładowania lub załadować ich obsługa <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
-   Wiele zestawów o tej samej tożsamości bez kontekstu ładowania może spowodować problemy tożsamości typu podobne do spowodowanych przez ładowanie zestawów o tej samej tożsamości do wielu kontekstów. Zobacz [uniknąć podczas ładowania zestawu do wielu kontekstów](#avoid_loading_into_multiple_contexts).  
  
-   Jeśli zestaw obrazu macierzystego, nie jest używane.  
  
-   Nie można załadować zestawu jako neutralne dla domen.  
  
-   W wersji systemu .NET Framework 1.0 i 1.1 nie są stosowane zasady.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Unikaj powiązanie nazwy zestawu z częściowa  
 Powiązanie z częściowa nazwa występuje po określeniu tylko części nazwy wyświetlanej zestawu (<xref:System.Reflection.Assembly.FullName%2A>) podczas ładowania zestawu. Na przykład może wywołać <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody za pomocą tylko prosta nazwa zestawu, pomijając wersję, kulturę i token klucza publicznego. Lub może wywołać <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody, który po raz pierwszy wywołuje <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody i w przypadku niepowodzenia można znaleźć zestawu wyszukiwania w pamięci podręcznej GAC i ładuje najnowszej dostępnej wersji zestawu.  
  
 Powiązanie z częściowa nazwa może spowodować wiele problemów, takie jak następujące:  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Metody może załadować inny zestaw o tej samej prostej nazwie. Na przykład dwie aplikacje mogą zainstalować dwóch zupełnie różnych zestawów czy mają prostą nazwę `GraphicsLibrary` w globalnej pamięci podręcznej zestawów.  
  
-   Zestaw został załadowany w rzeczywistości może nie być zgodny z poprzednimi wersjami. Na przykład nieokreślenie wersji może spowodować ładowanie dużo nowszą wersję niż wersja programu został początkowo zapisywane do użycia. Zmiany w nowszej wersji może spowodować błędy w aplikacji.  
  
-   Zestaw został załadowany w rzeczywistości może nie być zgodne z nowszymi. Na przykład może mieć wbudowane i przetestować aplikację do najnowszej wersji zestawu, ale powiązanie z częściowa może załadować znacznie starszą wersję, która nie zawiera funkcje, które korzysta z aplikacji.  
  
-   Instalowanie nowej aplikacji mogą być dzielone istniejących aplikacji. Aplikacja, która używa <xref:System.Reflection.Assembly.LoadWithPartialName%2A> — metoda może przerwane przez instalację nowszej, niezgodnej wersji zestaw udostępnionego.  
  
-   Może wystąpić nieoczekiwany zależności ładowania. Załadować tego udziału zależność ładowaniem ich z częściowa powiązania może spowodować w jednym zestawie za pomocą składnika, który nie był dwa zestawy wbudowanych lub przetestowana.  
  
 Z powodu problemów może spowodować <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metody zostało oznaczone jako przestarzałe. Firma Microsoft zaleca użycie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> — metoda i określ nazwy wyświetlane pełnego zestawu. Zobacz [zrozumieć zalety i wady kontekstów obciążenia](#load_contexts) i [rozważ przejście na domyślnym kontekście ładowania](#switch_to_default).  
  
 Jeśli chcesz użyć <xref:System.Reflection.Assembly.LoadWithPartialName%2A> — metoda ponieważ zapewnia łatwe i ładowania zestawu należy wziąć pod uwagę że o aplikacji zakończyć się niepowodzeniem z komunikatem o błędzie, który identyfikuje brakujący zestaw prawdopodobnie lepsze środowisko pracy użytkownika niż automatycznie za pomocą Nieznana wersja zestawu, który może spowodować nieprzewidywalne zachowanie i zabezpieczeń luk.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Unikaj ładowania zestawu do wielu kontekstów  
 Podczas ładowania zestawu do wielu kontekstów może spowodować problemy tożsamości typu. Jeśli ten sam typ jest załadowany z tego samego zestawu do dwóch różnych kontekstach, są tak, jakby został załadowany dwa różne typy o takiej samej nazwie. <xref:System.InvalidCastException> Jest generowany przy próbie rzutowania typu do innych komunikatem mylące wpisz `MyType` nie można rzutować na typ `MyType`.  
  
 Na przykład, załóżmy, że `ICommunicate` interfejsu jest zadeklarowany w zestawie o nazwie `Utility`, który jest przywoływany przez program, a także innych zestawów ładowanych w programie. Typy implementujące zawierają inne zestawy `ICommunicate` interfejsu, dzięki czemu program z nich korzystać.  
  
 Teraz należy rozważyć, co się stanie po uruchomieniu programu. Zestawy, do których odwołuje się program zostały załadowane w domyślnym kontekście ładowania. Załadowanie zestawu docelowego przez swoją tożsamość, za pomocą <xref:System.Reflection.Assembly.Load%2A> metody, będzie w domyślnym kontekście ładowania, a więc będzie jego zależności. Zarówno program i zestaw docelowy będzie używać tego samego `Utility` zestawu.  
  
 Jednak Załóżmy, że ładowanie zestawu docelowego za pomocą ścieżki pliku za pomocą <xref:System.Reflection.Assembly.LoadFile%2A> metody. Zestaw jest załadowany bez żadnego kontekstu, więc jego zależności nie są ładowane automatycznie. Program obsługi może być <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby podać zależności, a może załadować `Utility` zestawu z żadnego kontekstu za pomocą <xref:System.Reflection.Assembly.LoadFile%2A> — metoda. Teraz podczas tworzenia wystąpienia typu, który jest zawarty w zestawie docelowym i spróbuj przypisać je do zmiennej typu `ICommunicate`, <xref:System.InvalidCastException> jest generowany, gdy uzna środowiska uruchomieniowego `ICommunicate` interfejsy w dwóch kopii `Utility` zestawu do różnych typów.  
  
 Istnieje wiele innych scenariuszy, w których może być załadowany do wielu kontekstów zestawu. Najlepszym rozwiązaniem jest unikanie konfliktów przemieszczanie zestawu docelowego w ścieżce aplikacji, a następnie użyć <xref:System.Reflection.Assembly.Load%2A> metodę o nazwie wyświetlanej pełna. Zestaw jest następnie ładowany w domyślnym kontekście ładowania, a oba zestawy używać tego samego `Utility` zestawu.  
  
 Jeśli zestaw docelowy musi pozostać poza ścieżki aplikacji, możesz użyć <xref:System.Reflection.Assembly.LoadFrom%2A> metodę, aby załadować do kontekst load-from. Jeśli zestaw docelowy został skompilowany z odwołaniem do aplikacji `Utility` zestawu, zostanie użyty `Utility` zestawu, który aplikacja została załadowana w domyślnym kontekście ładowania. Należy pamiętać, że mogą wystąpić problemy, jeśli zestaw docelowy ma zależność kopii `Utility` zestawu znajdujących się poza ścieżki aplikacji. Jeśli ten zestaw jest ładowany w kontekście ładowania z przed obciążenia Twojej aplikacji `Utility` zestawu, obciążenia aplikacji nie powiedzie się.  
  
 [Rozważ przełączenie do kontekstu ładowania domyślne](#switch_to_default) sekcji omówiono rozwiązań alternatywnych, takich jak przy użyciu obciążeń ścieżka pliku <xref:System.Reflection.Assembly.LoadFile%2A> i <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Unikaj ładowania wielu wersji zestawu do tego samego kontekstu  
 Podczas ładowania wielu wersji zestawu do jednego kontekstu ładowania może spowodować problemy tożsamości typu. Jeśli ten sam typ jest załadowany z dwie wersje tego samego zestawu, są tak, jakby został załadowany dwa różne typy o takiej samej nazwie. <xref:System.InvalidCastException> Jest generowany przy próbie rzutowania typu do innych komunikatem mylące wpisz `MyType` nie można rzutować na typ `MyType`.  
  
 Na przykład program może załadować jednej wersji `Utility` zestawu bezpośrednio i później może załadować innego zestawu, który ładuje innej wersji `Utility` zestawu. Lub błąd kodowania może spowodować dwa różne ścieżki aplikacji do ładowania różnych wersji zestawu.  
  
 W domyślnym kontekście ładowania, ten problem może wystąpić, gdy używasz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodę i określić nazwy wyświetlane pełny zestaw, które obejmują różnych numerów wersji. Dla zestawów, które zostały załadowane bez kontekstu, problem może być spowodowane przy użyciu <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metodę, aby załadować ten sam zestaw z innej ścieżki. Środowisko uruchomieniowe uwzględnia dwa zestawy, które są ładowane z różne ścieżki się różnych zestawów, nawet jeśli ich tożsamości są takie same.  
  
 Oprócz typu tożsamości problemów, może spowodować wiele wersji zestawu <xref:System.MissingMethodException> Jeśli typ, który jest ładowany z jednej wersji zestawu są przekazywane do kodu, która oczekuje typu z innej wersji. Na przykład kod może oczekiwać, że metoda, która została dodana do nowszej wersji.  
  
 Więcej subtelnych błędów może wystąpić, jeśli zachowanie typu zmieniony między wersjami. Na przykład metoda może zgłosić wystąpił nieoczekiwany wyjątek lub zwrócić nieoczekiwaną wartość.  
  
 Uważnie przejrzyj swój kod, aby upewnić się, że tylko jeden jest załadowana wersja tego zestawu. Można użyć <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> metodę, aby określić, które zestawy są ładowane w danym momencie.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Rozważ przejście na domyślnym kontekście ładowania  
 Sprawdź wzorców obciążenia i wdrażania zestawu aplikacji. Pozwala wyeliminować zestawy, które są ładowane z tablic bajtowych Można przenieść zestawów do ścieżki próbkowania? Jeśli zestawy znajdują się w globalnej pamięci podręcznej zestawów lub w domenie aplikacji na ścieżce badania (to znaczy jego <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A>), można załadować zestawu przez jego tożsamość.  
  
 Jeśli nie jest możliwe umieszczenie ponownie zestawy w ścieżce sondowania, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak przy użyciu modelu dodatku programu .NET Framework, umieszczanie zestawów w globalnej pamięci podręcznej zestawów lub tworzenia domeny aplikacji.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Należy wziąć pod uwagę przy użyciu platformy .NET Framework — w modelu  
 Jeśli używasz kontekst load-from do zaimplementowania dodatków, które zwykle nie są zainstalowane w bazie danych aplikacji, użyj modelu dodatku .NET Framework. Ten model zapewnia izolację na poziomie domeny lub procesu aplikacji, bez konieczności samodzielnie zarządzać domen aplikacji. Aby uzyskać informacje na temat modelu dodatku, zobacz [dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Należy rozważyć użycie Globalna pamięć podręczna zestawów  
 Zestawy miejsca w pamięci podręcznej GAC można skorzystać z zalet ścieżki zestaw udostępnionego to poza aplikacją podstawowej, bez utraty korzyści wynikające z domyślnym kontekście ładowania lub pobieranie na wady innych kontekstach.  
  
### <a name="consider-using-application-domains"></a>Należy rozważyć użycie domeny aplikacji  
 Jeśli okaże się, że niektóre z zestawów nie można wdrożyć w ścieżce sondowania aplikacji, należy rozważyć utworzenie nowej domeny aplikacji dla tych zestawów. Użyj <xref:System.AppDomainSetup> do utworzenia nowej domeny aplikacji i użycia <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> właściwość, aby określić ścieżkę zawierającą zestawy chcesz załadować. Jeśli masz wiele katalogów do sondowania, możesz ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> do katalogu głównego i użyj <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> właściwość do identyfikacji podkatalogi do sondowania. Alternatywnie możesz utworzyć wiele domen aplikacji i ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> każdej domeny aplikacji odpowiednią ścieżkę do jego zestawów.  
  
 Należy pamiętać, że można użyć <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodę, aby załadować te zestawy. Ponieważ teraz są ścieżki próbkowania, zostaną one załadowane w domyślnym kontekście ładowania zamiast kontekst load-from. Jednak firma Microsoft zaleca, aby przełączyć się do <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> — metoda i dostarczanie pełnej nazwy wyświetlane zestawu, aby upewnić się, że poprawne wersje są zawsze używane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
 [Dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md)
