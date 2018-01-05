---
title: "Opakowanie i wdrażanie zasobów w aplikacjach klasycznych"
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
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f170c3e7174b231153a9e201f617faa786291056
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>Opakowanie i wdrażanie zasobów w aplikacjach klasycznych
Aplikacje polegają na .NET Framework Menedżera zasobów, reprezentowany przez <xref:System.Resources.ResourceManager> klasy można pobrać zlokalizowanych zasobów. Menedżer zasobów przyjęto, że model gwiazdy jest używany pakiet i wdrażanie zasobów. Koncentrator jest główny zestaw zawierający kod wykonywalny nonlocalizable i zasoby dla pojedynczego kultury, nazywany zero lub domyślną kulturę. Domyślną kulturę jest kultury rezerwowej dla aplikacji; jest kultura, którego zasoby są używane, jeśli nie można odnaleźć zlokalizowanych zasobów. Każdy gwiazdy łączy zestawu satelickiego, który zawiera zasoby dla kultury pojedynczego, ale nie zawiera żadnego kodu.  
  
 Ma kilka zalet do tego modelu:  
  
-   Po wdrożeniu aplikacji, można stopniowego dodawania zasobów dla nowych kultur. Ponieważ dalszy rozwój specyficzne dla kultury zasobów może wymagać dużo czasu, umożliwia to najpierw wersji głównej aplikacji i dostarczanie zasobów określonej kultury w późniejszym terminie.  
  
-   Możesz zaktualizować i zmienić zestawy satelickie aplikacji bez konieczności ponownego kompilowania aplikacji.  
  
-   Aplikacja musi załadować tylko te zestawy satelickie, które zawierają zasoby potrzebne dla określonej kultury. To znacznie zmniejszyć użycie zasobów systemowych.  
  
 Istnieją jednak również wady do tego modelu:  
  
-   Należy zarządzać wiele zestawów zasobów.  
  
-   Zwiększa koszt początkowy środka testowania aplikacji, ponieważ konieczne jest przetestowanie kilka konfiguracji. Należy pamiętać, że w długim okresie będzie łatwiejsze i tańsze do testowania jedną podstawową aplikację z kilku satelity, niż można przetestować i obsługa kilku wersji międzynarodowej równoległych.  
  
## <a name="resource-naming-conventions"></a>Konwencje nazewnictwa zasobów  
 Podczas pakowania aplikacji zasobów, nazwę je za pomocą konwencji nazewnictwa zasobów, które oczekuje środowisko uruchomieniowe języka wspólnego. Środowisko uruchomieniowe identyfikuje zasobu na podstawie nazwy kultury. Każdy kultury otrzymuje unikatową nazwę, która zwykle jest kombinacją nazwy kultury dwie litery, małe litery skojarzone z językiem i w razie potrzeby, nazwa przeszczepiania dwie litery, wielkie litery skojarzone z kraju lub regionu. Następuje nazwa przeszczepiania nazwę kultury oddzielonymi łącznikiem (-). Przykładami ja-JP w języku japońskim, ponieważ używany w Japonii, pl pl dla języka angielskiego, ponieważ używany w Stanach Zjednoczonych, de-DE na język niemiecki, ponieważ używany w Niemczech lub de-AT na język niemiecki, ponieważ używany w Austrii. Zobacz [dokumentacja interfejsu API National obsługi Language (NLS)](http://go.microsoft.com/fwlink/?LinkId=200048) w Przejdź globalne Developer Center pełną listę nazw kultur.  
  
> [!NOTE]
>  Aby uzyskać informacje o tworzeniu plików zasobów, zobacz [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) i [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Proces bazowy zasobu  
 Model gwiazdy dla opakowanie i wdrażanie zasobów używa rezerwowej procesu można znaleźć odpowiednich zasobów. Jeśli aplikacja zażąda zlokalizowanych zasobów, która jest niedostępna, środowisko uruchomieniowe języka wspólnego wyszukuje hierarchii kultur odpowiedni zasób rezerwowej, najlepiej pasującą do aplikacji przez użytkownika do żądania i zgłasza wyjątek tylko jako w ostateczności. Na każdym poziomie hierarchii Jeśli odpowiedni zasób zostanie znaleziony, środowisko uruchomieniowe używa jej. Jeśli zasób nie zostanie znaleziony, wyszukiwanie jest kontynuowane na następny poziom.  
  
 Aby poprawić wydajność wyszukiwania, zastosuj <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu do używanego zestawu głównego i przekaż go nazwa niezależnym od języka, który będzie współpracować z zestawu głównego.  
  
> [!TIP]
>  Można użyć [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) element konfiguracji, aby zoptymalizować proces rezerwowy zasobów i proces, za pomocą którego środowisko uruchomieniowe sondy dla zestawów zasobów. Aby uzyskać więcej informacji, zobacz [optymalizacja procesu powrotu zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) sekcji.  
  
 Zasób, do którego jest proces rezerwowy obejmuje następujące kroki:  
  
1.  Środowisko uruchomieniowe najpierw sprawdza, czy [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md) dla zestawu, który odpowiada żądaną kulturę dla aplikacji.  
  
     Zestawy zasobów, które są współużytkowane przez wiele aplikacji mogą być przechowywane w pamięci podręcznej GAC. To zwalnia z konieczności dołączania określone zestawy zasobów w każdej aplikacji, które możesz utworzyć struktury katalogu. Jeśli środowisko uruchomieniowe wykryje odwołanie do zestawu, wyszukuje zestawu dla żądanego zasobu. Jeśli znajdzie wejścia w zestawie używa żądanego zasobu. Jeśli nie znajdzie wpis kontynuuje wyszukiwanie.  
  
2.  Środowisko uruchomieniowe następnym razem katalog zawierający obecnie wykonywany zestaw do katalogu, który odpowiada żądaną kulturę. Jeśli znajdzie katalogu wyszukuje tego katalogu w zestawie prawidłowego satelity dla żądaną kulturę. Środowisko uruchomieniowe wyszukuje zestawu satelickiego dla żądanego zasobu. Jeśli znajdzie zasobu w zestawie, używa go. Jeśli nie znajdzie zasobu kontynuuje wyszukiwanie.  
  
3.  Środowisko uruchomieniowe kwerendę obok Instalatora Windows w celu określenia, czy zestawu satelickiego ma zostać zainstalowany na żądanie. Jeśli tak, obsługuje on instalacji, ładuje zestaw, a na koniec przeszukuje lub żądanego zasobu. Jeśli znajdzie zasobu w zestawie, używa go. Jeśli nie znajdzie zasobu kontynuuje wyszukiwanie.  
  
4.  Środowisko uruchomieniowe zgłasza <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można odnaleźć zestawu satelickiego. Wybranie obsłuż zdarzenie obsługi zdarzenia można zwraca odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie zwraca program obsługi zdarzeń `null` , aby kontynuować wyszukiwanie.  
  
5.  Wyszukiwanie następnego środowiska uruchomieniowego Globalna pamięć podręczna zestawów ponownie, ten czas dla zestawu nadrzędnego z żądanych kultury. Jeśli istnieje nadrzędnego zestawu w globalnej pamięci podręcznej zestawów, środowisko uruchomieniowe wyszukuje zestawu dla żądanego zasobu.  
  
     Kultura nadrzędna jest zdefiniowany jako odpowiednie kultury rezerwowej. Należy wziąć pod uwagę nadrzędnych jako kandydatów rezerwowej, ponieważ warunkiem, że dowolnego zasobu jest zgłaszanie wyjątku. Ten proces umożliwia do ponownego użycia zasobów. Tylko wtedy, gdy kultury podrzędnej nie potrzebuje do zlokalizowania żądanego zasobu, należy uwzględnić określonego zasobu na poziomie nadrzędnym. Na przykład, jeśli podane zestawy satelickie dla en (neutralne w języku angielskim) en-GB (w języku angielskim jak używany na brytyjski) i en US (angielski, ponieważ używany w Stanach Zjednoczonych), satelity en zawiera typowe satelitów terminologii i en-GB i en US można podać zastąpień dla tych warunków, które różnią się.  
  
6.  Środowisko uruchomieniowe następnym razem katalog zawierający obecnie wykonywany zestaw, aby zobaczyć, czy zawiera katalog nadrzędny. Jeśli istnieje katalog nadrzędny, środowisko uruchomieniowe wyszukuje katalogu w zestawie prawidłowego satelity dla kultury nadrzędnej. Jeśli znajdzie zestawu środowiska wykonawczego wyszukuje zestawu dla żądanego zasobu. Jeśli znajdzie zasobu, używa go. Jeśli nie znajdzie zasobu kontynuuje wyszukiwanie.  
  
7.  Środowisko uruchomieniowe kwerendę obok Instalatora Windows w celu określenia, czy zestawu satelickiego nadrzędny ma zostać zainstalowany na żądanie. Jeśli tak, obsługuje on instalacji, ładuje zestaw, a na koniec przeszukuje lub żądanego zasobu. Jeśli znajdzie zasobu w zestawie, używa go. Jeśli nie znajdzie zasobu kontynuuje wyszukiwanie.  
  
8.  Środowisko uruchomieniowe zgłasza <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można odnaleźć odpowiedniego zasobu rezerwowego. Wybranie obsłuż zdarzenie obsługi zdarzenia można zwraca odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie zwraca program obsługi zdarzeń `null` , aby kontynuować wyszukiwanie.  
  
9. Wyszukiwanie następnego środowiska uruchomieniowego nadrzędnych zestawy, tak jak poprzednie trzy kroki przez wiele potencjalnych poziomów. Każdy kulturę tylko jednego zdarzenia nadrzędnego, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwości, ale element nadrzędny może być swoim własnym działaniem nadrzędnym. Wyszukaj nadrzędnego kulturami zatrzymuje się podczas kultury <xref:System.Globalization.CultureInfo.Parent%2A> zwraca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; dla zasobu rezerwowy Niezmienna kultura nie jest uważana za nadrzędnego kultury lub kultury, który może mieć zasobów.  
  
10. Jeśli nadal nie można odnaleźć zasobu Przeszukano kultura, która pierwotnie została określona i wszystkich elementów nadrzędnych, zasobów dla kultury domyślnej (rezerwowy) jest używany. Zazwyczaj zasobów dla kultury domyślnej znajdują się w zestawie głównym aplikacji. Jednak można określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> właściwość <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut, aby wskazać, że ultimate rezerwowej lokalizacji zasobów jest zestaw satelicki, a nie głównego zestawu.  
  
    > [!NOTE]
    >  Zasób domyślny jest tylko zasób, który może zostać skompilowany w zestawie głównym. O ile nie zostanie określona przy użyciu zestawu satelickiego <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu jest powrotu ultimate (końcowy element nadrzędny). Dlatego zaleca się zawsze uwzględnić domyślny zestaw zasobów w Twojej główny zestaw. Pomaga to zapobiec wyjątki od został zgłoszony. Poprzez włączenie domyślnego zasobów plik Podaj rezerwowe dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób znajduje się zawsze dla użytkownika, nawet jeśli nie dotyczy kulturalnie.  
  
11. Na koniec, jeśli środowisko uruchomieniowe nie znajdzie zasobu dla domyślną kulturę (rezerwowy) <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException> jest zwracany wyjątek, aby wskazać, że nie można odnaleźć zasobu.  
  
 Na przykład załóżmy, że żądania aplikacji zasobu zlokalizowane dla języka hiszpańskiego (Meksyk) (kultury es MX). Środowisko uruchomieniowe najpierw szuka Globalna pamięć podręczna zestawów zestawu, który odpowiada es-MX, ale nie można go odnaleźć. Środowisko uruchomieniowe przeszuka katalog zawierający obecnie wykonywany zestaw dla katalogu es MX. Kończą się niepowodzeniem, środowiska uruchomieniowego wyszukiwania w globalnej pamięci podręcznej zestawów ponownie dla zestawu nadrzędnego, które odzwierciedla odpowiednie kultury rezerwowej — w tym przypadku es (wersja hiszpańska). Jeśli nie odnaleziono zestawu nadrzędnego, środowiska uruchomieniowego przeszukuje wszystkie poziomy potencjalnych zestawów nadrzędnego dla kultury es MX aż do znalezienia odpowiednich zasobów. Jeśli zasób nie zostanie odnaleziony, środowisko uruchomieniowe używa zasobów dla kultury domyślnej.  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>Optymalizowanie procesu bazowego zasobu  
 W następujących warunkach Aby zoptymalizować proces, za pomocą którego środowisko uruchomieniowe wyszukiwania zasobów w zestawy satelickie  
  
-   Zestawy satelickie są wdrażane w tej samej lokalizacji co zestaw kodu. Jeśli zainstalowano zestaw kodu w [Global Assembly Cache](../../../docs/framework/app-domains/gac.md), zestawy satelickie są również zainstalowane w globalnej pamięci podręcznej zestawów. Po zainstalowaniu zestawu kodu w katalogu zestawy satelickie są instalowane w folderach specyficzne dla kultury tego katalogu.  
  
-   Zestawy satelickie nie są zainstalowane na żądanie.  
  
-   Kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
 Zoptymalizować badanie zestawów satelickich umieszczając [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) elementu i ustawienie jej `enabled` atrybutu `true` w pliku konfiguracyjnym aplikacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 Zoptymalizowane sondowania zestawów satelickich jest funkcji opcjonalnych. Oznacza to, że środowisko uruchomieniowe wykonuje kroki opisane w temacie [procesu powrotu zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) chyba że [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) element jest obecny w aplikacji plik konfiguracji i jego `enabled` atrybut ma ustawioną `true`. Jeśli jest to możliwe, proces badania zestawu satelickiego zmienia się w następujący sposób:  
  
-   Środowisko uruchomieniowe używa lokalizacji nadrzędnego zestawu kodu do sondowania dla zestawu satelickiego. Jeśli zestaw nadrzędny jest zainstalowany w globalnej pamięci podręcznej zestawów, środowisko uruchomieniowe sondy w pamięci podręcznej, ale nie w katalogu aplikacji. Jeśli zestaw nadrzędny jest zainstalowany w katalogu aplikacji, środowisko uruchomieniowe sondy w katalogu aplikacji, ale nie znajduje się w globalnej pamięci podręcznej zestawów.  
  
-   Środowisko uruchomieniowe nie zapytania dla zestawów satelickich na żądanie instalacji Instalatora Windows.  
  
-   W przypadku niepowodzenia sondowania dla zestawu określonego zasobu środowiska uruchomieniowego nie wygenerował <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>Ostateczny powrót do zestawu satelickiego  
 Opcjonalnie można usunąć zasoby z głównego zestawu i określić, środowiska uruchomieniowego powinna załadować zasobów ostatecznej rezerwy z zestawu satelickiego, który odpowiada określoną kulturę. Aby kontrolować proces rezerwowy, należy użyć <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> Konstruktor i podać wartość <xref:System.Resources.UltimateResourceFallbackLocation> parametr, który określa, czy Menedżer zasobów należy wyodrębnić zasoby rezerwowe z główny zestaw lub zestawu satelickiego.  
  
 W poniższym przykładzie użyto <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut do przechowywania aplikacji zasoby ostatecznej rezerwy w zestawie satelickim język francuski (fr).  Przykład ma dwa pliki zasobów na podstawie tekstu definiujące będący pojedynczym ciągiem zasób o nazwie `Greeting`. Po pierwsze, resources.fr.txt, zawiera zasób języka francuskiego.  
  
```  
Greeting=Bon jour!  
```  
  
 Drugi, resources,ru.txt, zawiera zasób języka rosyjskiego.  
  
```  
Greeting=Добрый день  
```  
  
 Te dwa pliki są kompilowane do plików .resources, uruchamiając [generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) z wiersza polecenia.  Dla zasobu języka francuskiego to polecenie jest:  
  
 **ResGen.exe resources.fr.txt**  
  
 Dla zasobu języka rosyjskiego polecenie jest:  
  
 **ResGen.exe resources.ru.txt**  
  
 .resources — pliki są osadzone w biblioteki dołączanej dynamicznie, uruchamiając [konsolidator zestawów (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) polecenia wiersza dla zasobu języka francuskiego w następujący sposób:  
  
 **Al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 i zasobu języka rosyjskiego w następujący sposób:  
  
 **Al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Kod źródłowy aplikacji znajduje się w pliku o nazwie Example1.cs lub Example1.vb. Obejmuje on <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu, aby wskazać, czy domyślny zasób aplikacji znajduje się w podkatalogu fr. Tworzy wystąpienie Menedżera zasobów, pobiera wartość `Greeting` zasobów i wyświetla je w konsoli.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Następnie można skompilować kodu źródłowego C# z wiersza polecenia w następujący sposób:  
  
 **CSC Example1.cs**  
  
 To polecenie dla kompilatora języka Visual Basic jest bardzo podobne:  
  
 **vbc — Example1.vb**  
  
 Ponieważ nie ma żadnych zasobów, osadzony w zestawie głównym, nie masz skompilować przy użyciu `/resource` przełącznika.  
  
 Po uruchomieniu przykładzie z systemu, w której język jest inna niż rosyjski wyświetla następujące dane wyjściowe:  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>Sugerowane alternatywne opakowanie  
 Ograniczenia czasu lub budżetu może uniemożliwić tworzenie zestaw zasobów dla każdego przeszczepiania, który obsługuje aplikacja. Zamiast tego można utworzyć pojedynczego satelicki kultury nadrzędnej, czy wszystkie powiązane podhodowli może użyć. Na przykład można udostępnić pojedynczy angielskiej wersji językowej satelicki (en) pobieranych przez użytkowników, którzy żądają określonego regionu angielskiej wersji językowej zasobów oraz pojedynczego niemieckim satelicki (de) dla użytkowników, którzy żądają zasobów niemieckim określonego regionu. Na przykład żądań na język niemiecki jako używany w Niemczech (de-DE) Austrii (de-AT) i Szwajcarii (de-CH) może spowodować powrót do zestawu satelickiego niemiecki (de). Zasoby domyślne są końcowego powrotu i w związku z tym powinny być zasoby, które będzie wymagane przez większość użytkowników aplikacji, więc wybrać dokładnie te zasoby. Takie podejście wdraża zasobów, które są mniej kulturalnie określonych, ale można znacznie zmniejszyć koszty lokalizacja aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
