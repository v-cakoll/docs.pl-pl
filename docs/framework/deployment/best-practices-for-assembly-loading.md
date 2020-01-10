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
ms.openlocfilehash: d1b6c2cd9f96a4acf48cbced48a86bc3e3409562
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716587"
---
# <a name="best-practices-for-assembly-loading"></a>Najlepsze praktyki dotyczące ładowania zestawu
W tym artykule omówiono sposoby uniknięcia problemów z tożsamością typu, które mogą prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>i innych błędów. W tym artykule omówiono następujące zalecenia:  
  
- [Zapoznaj się z zaletami i wadami kontekstów ładowania](#load_contexts)  
  
- [Unikaj tworzenia powiązań dla częściowych nazw zestawów](#avoid_partial_names)  
  
- [Unikanie ładowania zestawu do wielu kontekstów](#avoid_loading_into_multiple_contexts)  
  
- [Unikaj ładowania wielu wersji zestawu do tego samego kontekstu](#avoid_loading_multiple_versions)  
  
- [Rozważ przełączenie do domyślnego kontekstu ładowania](#switch_to_default)  
  
 Pierwsze zalecenie, [zrozumiałe zalety i wady kontekstów ładowania](#load_contexts), zawiera ogólne informacje na temat innych zaleceń, ponieważ wszystkie zależą od znajomości kontekstów ładowania.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Zapoznaj się z zaletami i wadami kontekstów ładowania  
 W domenie aplikacji zestawy mogą być ładowane do jednego z trzech kontekstów lub mogą być ładowane bez kontekstu:  
  
- Domyślny kontekst ładowania zawiera zestawy znalezione przez sondowanie globalnej pamięci podręcznej zestawów, magazyn zestawów hosta, jeśli środowisko uruchomieniowe jest hostowane (na przykład w SQL Server) i <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> domeny aplikacji. Większość przeciążenia metody <xref:System.Reflection.Assembly.Load%2A> ładowania zestawów do tego kontekstu.  
  
- Kontekst ładowania z zawiera zestawy, które są ładowane z lokalizacji, które nie są przeszukiwane przez moduł ładujący. Na przykład, dodatki mogą być zainstalowane w katalogu, który nie znajduje się w ścieżce aplikacji. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>i <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> są przykładami metod, które ładują się według ścieżki.  
  
- Kontekst tylko odbicia zawiera zestawy ładowane przy użyciu metod <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>. Nie można wykonać kodu w tym kontekście, dlatego nie jest on omawiany w tym miejscu. Aby uzyskać więcej informacji, zobacz [instrukcje: ładowanie zestawów do kontekstu przeznaczonego tylko do odbicia](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Jeśli wygenerowałeś tymczasowy zestaw dynamiczny przy użyciu emisji odbicia, zestaw nie jest w żadnym kontekście. Ponadto większość zestawów, które są ładowane przy użyciu metody <xref:System.Reflection.Assembly.LoadFile%2A> są ładowane bez kontekstu, a zestawy, które są ładowane z tablic bajtowych są ładowane bez kontekstu, chyba że ich tożsamość (po zastosowaniu zasad) ustali, że znajdują się w globalnej pamięci podręcznej zestawów.  
  
 Konteksty wykonywania mają zalety i wady, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="default-load-context"></a>Domyślny kontekst ładowania  
 Gdy zestawy są ładowane do domyślnego kontekstu ładowania, ich zależności są ładowane automatycznie. Zależności, które są ładowane do domyślnego kontekstu ładowania, są automatycznie dostępne dla zestawów w domyślnym kontekście ładowania lub w kontekście ładowania z. Ładowanie przez tożsamość zestawu zwiększa stabilność aplikacji przez zapewnienie, że nieznane wersje zestawów nie są używane (zobacz sekcję [Unikaj tworzenia powiązań dla częściowych nazw zestawów](#avoid_partial_names) ).  
  
 Użycie domyślnego kontekstu ładowania ma następujące wady:  
  
- Zależności, które są ładowane do innych kontekstów, są niedostępne.  
  
- Nie można załadować zestawów z lokalizacji poza ścieżką sondy do domyślnego kontekstu ładowania.  
  
### <a name="load-from-context"></a>Kontekst ładowania z  
 Kontekst załadowania umożliwia załadowanie zestawu ze ścieżki, która nie znajduje się pod ścieżką aplikacji i w związku z tym nie jest uwzględniona w trakcie sondowania. Pozwala na zlokalizowanie i załadowanie zależności od tej ścieżki, ponieważ informacje o ścieżce są obsługiwane przez kontekst. Ponadto zestawy w tym kontekście mogą korzystać z zależności, które są ładowane do domyślnego kontekstu ładowania.  
  
 Ładowanie zestawów przy użyciu metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub jednej z innych metod, które ładują według ścieżki, ma następujące wady:  
  
- Jeśli zestaw o tej samej tożsamości jest już załadowany, <xref:System.Reflection.Assembly.LoadFrom%2A> zwraca załadowany zestaw, nawet jeśli określono inną ścieżkę.  
  
- Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>, a później zestaw w domyślnym kontekście ładowania podejmie próbę załadowania tego samego zestawu według nazwy wyświetlanej, próba załadowania zakończy się niepowodzeniem. Taka sytuacja może wystąpić w przypadku deserializacji zestawu.  
  
- Jeśli zestaw jest ładowany z <xref:System.Reflection.Assembly.LoadFrom%2A>, a ścieżka sondowania zawiera zestaw o tej samej tożsamości, ale w innej lokalizacji, może wystąpić <xref:System.InvalidCastException>, <xref:System.MissingMethodException>lub inne nieoczekiwane zachowanie.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> wymaga <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> i <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>lub <xref:System.Net.WebPermission>, w określonej ścieżce.  
  
- Jeśli istnieje obraz natywny dla zestawu, nie jest on używany.  
  
- Zestawu nie można załadować jako neutralnego dla domeny.  
  
- W .NET Framework wersje 1,0 i 1,1 zasady nie są stosowane.  
  
### <a name="no-context"></a>Brak kontekstu  
 Ładowanie bez kontekstu jest jedyną opcją dla zestawów przejściowych, które są generowane przy użyciu emisji odbicia. Ładowanie bez kontekstu jest jedynym sposobem ładowania wielu zestawów, które mają taką samą tożsamość w jednej domenie aplikacji. Należy unikać kosztu sondowania.  
  
 Zestawy, które są ładowane z tablic bajtowych, są ładowane bez kontekstu, chyba że tożsamość zestawu, który jest ustanowiony, gdy zasady są stosowane, dopasowuje tożsamość zestawu w globalnej pamięci podręcznej zestawów; w takim przypadku zestaw jest ładowany z globalnej pamięci podręcznej zestawów.  
  
 Ładowanie zestawów bez kontekstu ma następujące wady:  
  
- Inne zestawy nie mogą być powiązane z zestawami, które są ładowane bez kontekstu, chyba że obsłużysz zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
- Zależności nie są ładowane automatycznie. Można wstępnie załadować je bez kontekstu, załadować je do domyślnego kontekstu ładowania lub załadować je przez obsługę zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
- Ładowanie wielu zestawów o tej samej tożsamości bez kontekstu może powodować problemy z tożsamościami typu podobne do tych spowodowanych przez ładowanie zestawów o tej samej tożsamości w wielu kontekstach. Zobacz [unikanie ładowania zestawu do wielu kontekstów](#avoid_loading_into_multiple_contexts).  
  
- Jeśli istnieje obraz natywny dla zestawu, nie jest on używany.  
  
- Zestawu nie można załadować jako neutralnego dla domeny.  
  
- W .NET Framework wersje 1,0 i 1,1 zasady nie są stosowane.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Unikaj tworzenia powiązań dla częściowych nazw zestawów  
 Powiązanie części nazwy występuje, gdy podczas ładowania zestawu zostanie określona tylko część nazwy wyświetlanej zestawu (<xref:System.Reflection.Assembly.FullName%2A>). Można na przykład wywołać metodę <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> tylko z prostą nazwą zestawu, pomijając wersję, kulturę i token klucza publicznego. Lub można wywołać metodę <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>, która najpierw wywołuje metodę <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> i, jeśli to nie powiodło się odnalezienie zestawu, przeszukuje globalną pamięć podręczną zestawów i ładuje najnowszą dostępną wersję zestawu.  
  
 Częściowe powiązanie nazw może spowodować wiele problemów, w tym następujące:  
  
- Metoda <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> może załadować inny zestaw o tej samej prostej nazwie. Na przykład dwie aplikacje mogą instalować dwa całkowicie różne zestawy, które mają prostą nazwę `GraphicsLibrary` w globalnej pamięci podręcznej zestawów.  
  
- Zestaw, który jest faktycznie załadowany, może nie być zgodny z poprzednimi wersjami. Na przykład nieokreślanie wersji może spowodować załadowanie znacznie późniejszej wersji niż wersja pierwotnie zapisywana przez program do użycia. Zmiany w nowszej wersji mogą powodować błędy w aplikacji.  
  
- Zestaw, który jest faktycznie załadowany, może nie być zgodny z przesyłaniem dalej. Na przykład aplikacja została skompilowana i przetestowana przy użyciu najnowszej wersji zestawu, ale częściowe powiązanie może ładować wiele wcześniejszych wersji, które nie są używane przez aplikację.  
  
- Zainstalowanie nowych aplikacji może spowodować przerwanie istniejących aplikacji. Aplikacja, która używa metody <xref:System.Reflection.Assembly.LoadWithPartialName%2A>, może być uszkodzona przez zainstalowanie nowszej, niezgodnej wersji zestawu udostępnionego.  
  
- Może wystąpić nieoczekiwane ładowanie zależności. Ładujesz dwa zestawy, które współużytkują zależność, ładując je za pomocą częściowego powiązania, może spowodować, że jeden zestaw będzie używany jako składnik, który nie został skompilowany lub przetestowany.  
  
 Ze względu na problemy, które może to spowodować, Metoda <xref:System.Reflection.Assembly.LoadWithPartialName%2A> została oznaczona jako przestarzała. Zaleca się, aby zamiast tego używać metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> i określić pełną nazwę wyświetlaną zestawu. Zapoznaj [się z tematem zalety i wady kontekstów ładowania](#load_contexts) i [Rozważ zmianę domyślnego kontekstu ładowania](#switch_to_default).  
  
 Jeśli chcesz użyć metody <xref:System.Reflection.Assembly.LoadWithPartialName%2A>, ponieważ sprawia to, że ładowanie zestawu jest łatwe, weź pod uwagę, że aplikacja nie powiedzie się z komunikatem o błędzie, który identyfikuje brakujący zestaw, może zapewnić lepszy interfejs użytkownika, niż automatycznie przy użyciu nieznanej wersji zestawu, co może spowodować nieprzewidywalne zachowanie i luki w zabezpieczeniach.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Unikanie ładowania zestawu do wielu kontekstów  
 Załadowanie zestawu do wielu kontekstów może spowodować problemy z tożsamościami typu. Jeśli ten sam typ jest ładowany z tego samego zestawu do dwóch różnych kontekstów, jest tak, jakby dwa różne typy o tej samej nazwie zostały załadowane. Zostanie wygenerowany <xref:System.InvalidCastException>, jeśli spróbujesz rzutować jeden typ na drugi, z komunikatem o mylącym typie `MyType` nie można rzutować na `MyType`typu.  
  
 Załóżmy na przykład, że interfejs `ICommunicate` jest zadeklarowany w zestawie o nazwie `Utility`, do którego odwołuje się program, a także inne zestawy, które program załaduje. Te inne zestawy zawierają typy implementujące interfejs `ICommunicate`, co pozwala programowi na ich używanie.  
  
 Teraz Rozważmy, co się dzieje, gdy program jest uruchomiony. Zestawy, do których odwołuje się program, są ładowane do domyślnego kontekstu ładowania. Jeśli załadujesz zestaw docelowy za pomocą jego tożsamości, przy użyciu metody <xref:System.Reflection.Assembly.Load%2A>, będzie on znajdować się w domyślnym kontekście ładowania i dlatego będzie jego zależnościami. Zarówno program, jak i zestaw docelowy będą używać tego samego zestawu `Utility`.  
  
 Zaleca się jednak, aby załadować zestaw docelowy według ścieżki pliku przy użyciu metody <xref:System.Reflection.Assembly.LoadFile%2A>. Zestaw jest ładowany bez żadnego kontekstu, więc jego zależności nie są ładowane automatycznie. Możesz mieć procedurę obsługi dla zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>, aby dostarczyć zależność, i może załadować zestaw `Utility` bez kontekstu przy użyciu metody <xref:System.Reflection.Assembly.LoadFile%2A>. Teraz podczas tworzenia wystąpienia typu, który jest zawarty w zestawie docelowym i próba przypisania go do zmiennej typu `ICommunicate`, zostanie zgłoszony <xref:System.InvalidCastException>, ponieważ środowisko uruchomieniowe traktuje interfejsy `ICommunicate` w dwóch kopiach zestawu `Utility` jako różne typy.  
  
 Istnieje wiele innych scenariuszy, w których zestaw może być ładowany do wielu kontekstów. Najlepszym rozwiązaniem jest uniknięcie konfliktów przez przelokalizowanie zestawu docelowego w ścieżce aplikacji i użycie metody <xref:System.Reflection.Assembly.Load%2A> z pełną nazwą wyświetlaną. Zestaw jest następnie ładowany do domyślnego kontekstu ładowania, a oba zestawy używają tego samego zestawu `Utility`.  
  
 Jeśli zestaw docelowy musi pozostać poza ścieżką aplikacji, można użyć metody <xref:System.Reflection.Assembly.LoadFrom%2A>, aby załadować go do kontekstu ładowania z. Jeśli zestaw docelowy został skompilowany za pomocą odwołania do zestawu `Utility` aplikacji, użyje zestawu `Utility`, który aplikacja została załadowana do domyślnego kontekstu ładowania. Należy pamiętać, że problemy mogą wystąpić, jeśli zestaw docelowy ma zależność od kopii zestawu `Utility` znajdującego się poza ścieżką aplikacji. Jeśli ten zestaw jest ładowany do kontekstu obciążenia przed załadowaniem zestawu `Utility` przez aplikację, ładowanie aplikacji zakończy się niepowodzeniem.  
  
 [Rozważ przełączenie się do domyślnej sekcji kontekstu ładowania](#switch_to_default) omawia alternatywy do używania ładowania ścieżki plików, takich jak <xref:System.Reflection.Assembly.LoadFile%2A> i <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Unikaj ładowania wielu wersji zestawu do tego samego kontekstu  
 Ładowanie wielu wersji zestawu do jednego kontekstu ładowania może spowodować problemy z tożsamościami typu. Jeśli ten sam typ jest ładowany z dwóch wersji tego samego zestawu, jest tak, jakby dwa różne typy o tej samej nazwie zostały załadowane. Zostanie wygenerowany <xref:System.InvalidCastException>, jeśli spróbujesz rzutować jeden typ na drugi, z komunikatem o mylącym typie `MyType` nie można rzutować na `MyType`typu.  
  
 Na przykład program może załadować jedną wersję zestawu `Utility` bezpośrednio, a później może załadować kolejny zestaw, który ładuje inną wersję zestawu `Utility`. Lub błąd kodowania może spowodować dwie różne ścieżki kodu w aplikacji, aby załadować różne wersje zestawu.  
  
 W domyślnym kontekście ładowania ten problem może wystąpić w przypadku użycia metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> i określenia kompletnych nazw wyświetlanych zestawu zawierających różne numery wersji. W przypadku zestawów, które są ładowane bez kontekstu, problem może być spowodowany użyciem metody <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> do załadowania tego samego zestawu z różnych ścieżek. Środowisko uruchomieniowe traktuje dwa zestawy, które są ładowane z różnych ścieżek, aby były różnymi zestawami, nawet jeśli ich tożsamości są takie same.  
  
 Oprócz problemów z tożsamościami, wiele wersji zestawu może spowodować <xref:System.MissingMethodException>, jeśli typ, który jest ładowany z jednej wersji zestawu, jest przenoszona do kodu, który oczekuje tego typu z innej wersji. Na przykład kod może oczekiwać metody, która została dodana do nowszej wersji.  
  
 Jeśli zachowanie typu uległo zmianie między wersjami, mogą wystąpić bardziej subtelne błędy. Na przykład metoda może zgłosić nieoczekiwany wyjątek lub zwrócić nieoczekiwaną wartość.  
  
 Uważnie Przejrzyj swój kod, aby upewnić się, że załadowana została tylko jedna wersja zestawu. Za pomocą metody <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> można określić, które zestawy są ładowane w danym momencie.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Rozważ przełączenie do domyślnego kontekstu ładowania  
 Sprawdź wzorce ładowania i wdrażania aplikacji. Czy można wyeliminować zestawy, które są ładowane z tablic bajtowych? Czy można przenieść zestawy do ścieżki Bing? Jeśli zestawy znajdują się w globalnej pamięci podręcznej zestawów lub w ścieżce do sondowania domeny aplikacji (czyli jej <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A>), można załadować zestaw według jego tożsamości.  
  
 Jeśli nie można umieścić wszystkich zestawów w ścieżce sondowania, należy rozważyć alternatywy, takie jak użycie modelu dodatku .NET Framework, umieszczenie zestawów w globalnej pamięci podręcznej zestawów lub utworzenie domen aplikacji.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Rozważ użycie modelu dodatku .NET Framework  
 Jeśli używasz kontekstu Załaduj-from do implementowania dodatków, które zwykle nie są zainstalowane w bazie aplikacji, użyj modelu dodatku .NET Framework. Ten model zapewnia izolację na poziomie domeny aplikacji lub procesu, bez konieczności samodzielnego zarządzania domenami aplikacji. Aby uzyskać informacje o modelu dodatków, zobacz [Dodatki i rozszerzalność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Rozważ użycie globalnej pamięci podręcznej zestawów  
 Umieść zestawy w globalnej pamięci podręcznej zestawów, aby uzyskać korzyści wynikające ze wspólnej ścieżki zestawu, która znajduje się poza bazą aplikacji, bez utraty korzyści wynikającej z domyślnego kontekstu ładowania lub wyłączania wad innych kontekstów.  
  
### <a name="consider-using-application-domains"></a>Rozważ użycie domen aplikacji  
 Jeśli okaże się, że niektóre zestawy nie mogą być wdrożone w ścieżce sondowania aplikacji, należy rozważyć utworzenie nowej domeny aplikacji dla tych zestawów. Użyj <xref:System.AppDomainSetup>, aby utworzyć nową domenę aplikacji, a następnie użyj właściwości <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>, aby określić ścieżkę zawierającą zestawy, które mają zostać załadowane. Jeśli masz wiele katalogów do sondowania, możesz ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> na katalog główny i użyć właściwości <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType>, aby zidentyfikować podkatalogi do sondowania. Alternatywnie można utworzyć wiele domen aplikacji i ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> poszczególnych domen aplikacji do odpowiedniej ścieżki dla zestawów.  
  
 Należy pamiętać, że można użyć metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> do załadowania tych zestawów. Ponieważ znajdują się one teraz w ścieżce do sondowania, zostaną one załadowane do domyślnego kontekstu ładowania zamiast kontekstu ładowania z. Zaleca się jednak przełączenie na metodę <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> i dostarczenie pełnych nazw wyświetlanych zestawu, aby upewnić się, że zawsze są używane poprawne wersje.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
