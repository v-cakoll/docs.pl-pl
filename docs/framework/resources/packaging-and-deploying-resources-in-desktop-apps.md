---
title: Opakowanie i wdrażanie zasobów w aplikacjach .NET
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74b9e23c65209c8084588d09670e3c64e44213
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493732"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Opakowanie i wdrażanie zasobów w aplikacjach .NET
Aplikacje polegają na .NET Framework Menedżera zasobów, reprezentowane przez <xref:System.Resources.ResourceManager> klasy w celu pobrania zlokalizowanych zasobów. Menedżer zasobów przyjęto założenie, że modelu topologi gwiaździstej umożliwia tworzenie pakietów i wdrażanie zasobów. Piasta to główny zestaw, który zawiera kod wykonywalny nielokalizowanych i zasoby dla jednej kultury, o nazwie zero lub kultury domyślnej. Domyślną kulturę używaną jest rezerwowego kulturą aplikacji; jest kultury, którego zasoby są używane, jeśli nie można odnaleźć zlokalizowanych zasobów. Każdej szprysze nawiązuje połączenie z zestawem satelickim, która zawiera zasoby dla jednej kultury, ale nie zawiera żadnego kodu.  
  
 Istnieje kilka zalet tego modelu:  
  
-   Po wdrożeniu aplikacji możesz stopniowo dodawać zasoby dla nowych języków. Ponieważ dalszy rozwój specyficznych dla kultury zasobów może wymagać znacznej ilości czasu, dzięki temu można najpierw wersji głównej aplikacji i dostarczenia specyficznych dla kultury zasobów w późniejszym terminie.  
  
-   Możesz zaktualizować i zmienić zestawy satelickie aplikacji bez konieczności ponownego kompilowania aplikacji.  
  
-   Aplikacja musi załadować tylko te zestawy satelickie, które zawierają zasoby wymagane dla danej kultury. Może to znacznie zmniejszyć użycia zasobów systemowych.  
  
 Istnieją jednak również wady do tego modelu:  
  
-   Muszą zarządzać wiele zestawów zasobów.  
  
-   Początkowy koszt testowania aplikacji zwiększa, ponieważ należy przetestować kilka konfiguracji. Należy pamiętać, że w długim okresie będzie łatwiejsze i mniej kosztowna przetestować jedną podstawową aplikację za pomocą kilku satelity, niż można przetestować i obsługa kilka wersji międzynarodowej równoległych.  
  
## <a name="resource-naming-conventions"></a>Konwencje nazewnictwa zasobów  
 Podczas pakowania zasobów aplikacji możesz nazwać je przy użyciu konwencji nazewnictwa zasobów, których oczekuje środowiska uruchomieniowego języka wspólnego. Środowisko uruchomieniowe identyfikuje zasób za pomocą nazwy kultury. Każda kultura otrzymuje unikatową nazwę, która zwykle jest kombinacją nazwy kultury dwie litery, małe litery, skojarzone z językiem i w razie potrzeby, nazwa przeszczepiania dwie litery, wielkie litery skojarzone z kraju lub regionu. Nazwa przeszczepiania jest zgodna nazwa kultury, oddzielone kreską (-). Przykłady obejmują ja-JP w języku japońskim, ponieważ używany w Japonii, en US, dla języka angielskiego, ponieważ używany w USA, de-DE, dla języka niemieckiego jak używany w Niemczech lub de-AT dla języka niemieckiego jak używany w Austria. Zobacz [National Language Support (NLS) API Reference](https://go.microsoft.com/fwlink/?LinkId=200048) w Centrum deweloperów Go Global pełną listę nazw kultur.  
  
> [!NOTE]
>  Aby uzyskać informacje o tworzeniu plików zasobów, zobacz [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) i [tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>Proces bazowy zasobu  
 Model gwiazdy do pakowania i wdrażania zasobów używa procesu bazowego można zlokalizować odpowiednich zasobów. Jeśli aplikacja żąda zlokalizowany zasób, który jest niedostępny, środowisko uruchomieniowe języka wspólnego wyszukuje hierarchii kultur odpowiedni zasób rezerwowy, która najlepiej pasuje do aplikacji użytkownika przez żądania i zgłasza wyjątek, tylko jako w ostateczności. Na każdym poziomie hierarchii Jeśli odpowiedni zasób zostanie znaleziony, środowisko wykonawcze używa go. Jeśli zasób nie zostanie znaleziony, wyszukiwanie jest kontynuowane na następnym poziomie.  
  
 Aby poprawić wydajność wyszukiwania, zastosuj <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu do swojego głównego zestawu i przekaż mu nazwę neutralny język, który będzie działać z zestawu głównego.  
  
### <a name="net-framework-resource-fallback-process"></a>Proces bazowy zasobu .NET framework
 Proces bazowy zasobu .NET Framework obejmuje następujące czynności:

> [!TIP]
>  Można użyć [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) element konfiguracji, aby zoptymalizować proces bazowy zasobu i proces, za pomocą której środowisko uruchomieniowe sondy zestawów zasobów. Aby uzyskać więcej informacji, zobacz [optymalizowanie procesu uwierzytelniania rezerwowego zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) sekcji.  
  
1.  Po pierwsze sprawdza środowisko uruchomieniowe [globalnej pamięci podręcznej](../../../docs/framework/app-domains/gac.md) dla zestawu, który odpowiada żądaną kulturę dla swojej aplikacji.  
  
     Zestawy zasobów, które są współużytkowane przez wiele aplikacji mogą być przechowywane w globalnej pamięci podręcznej. To zwalnia z konieczności dołączania określone zestawy zasobów w strukturze katalogów o każdej utworzonej aplikacji. Jeśli środowisko uruchomieniowe wykryje odwołanie do zestawu, wyszukuje zestaw dla żądanego zasobu. Jeśli znajdzie wejścia w zestawie używa żądanego zasobu. Jeśli wpis nie zostanie znaleziona, kontynuuje wyszukiwanie.  
  
2.  Środowisko uruchomieniowe sprawdza następnie katalog zawierający obecnie wykonywany zestaw dla podkatalogu, który odpowiada żądaną kulturę. Jeśli znajdzie podkatalogu, wyszukuje tym podkatalogu dla zestawu prawidłowego satelity dla żądanego kultury. Środowisko uruchomieniowe wyszukuje zestawu satelickiego dla żądanego zasobu. Jeśli znajdzie zasobu w zestawie używa go. Jeśli zasób nie zostanie znaleziona, kontynuuje wyszukiwanie.
  
3.  Środowisko uruchomieniowe obok kwerendy Instalatora Windows, aby określić, czy w zestawie satelickim można zainstalować na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw, a na koniec przeszukuje go lub żądany zasób. Jeśli znajdzie zasobu w zestawie używa go. Jeśli zasób nie zostanie znaleziona, kontynuuje wyszukiwanie.  
  
4.  Środowisko wykonawcze zgłasza <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można odnaleźć zestawu satelickiego. Jeśli wybierzesz obsłużyć zdarzenie, obsługi zdarzenia może zwrócić odwołanie do zestawu satelickiego, którego zasoby będzie służyć do wyszukiwania. W przeciwnym razie zwraca program obsługi zdarzeń `null` i wyszukiwanie jest kontynuowane.  
  
5.  Wyszukuje następny środowiska uruchomieniowego globalnej pamięci podręcznej ponownie, tym razem dla zestawu nadrzędnego żądaną kulturę. Jeśli istnieje nadrzędny zestawu w globalnej pamięci podręcznej, środowisko uruchomieniowe wyszukuje zestaw dla żądanego zasobu.  
  
     Kultura nadrzędna jest zdefiniowany jako odpowiednie kultury rezerwowej. Ponieważ warunkiem, że dowolny zasób jest zostanie zgłoszony wyjątek, należy wziąć pod uwagę elementów nadrzędnych, podczas tworzenia rezerwowego. Ten proces umożliwia do ponownego użycia zasobów. Określony zasób na poziomie nadrzędnym powinny obejmować tylko wtedy, gdy kultury podrzędnych nie trzeba lokalizować żądanego zasobu. Na przykład, jeśli użytkownik poda zestawów satelickich dla `en` (neutralny język angielski) `en-GB` (w języku angielskim jak używany w Wielkiej Brytanii), a `en-US` (w języku angielskim jak używany w Stanach Zjednoczonych), `en` satelitarnej zawiera typowe terminologii i `en-GB` i `en-US` satelity, mogły udostępnić zastąpień dla tych warunków, które różnią się.
  
6.  Środowisko uruchomieniowe sprawdza następnie katalog zawierający obecnie wykonywany zestaw, aby zobaczyć, czy zawiera on katalog nadrzędny. Jeśli w katalogu nadrzędnym istnieje, środowisko uruchomieniowe wyszukuje katalogu zestaw prawidłowego satelity dla kultury nadrzędnej. Jeśli znajdzie zestawu, środowisko uruchomieniowe wyszukuje zestaw dla żądanego zasobu. Jeśli znajdzie zasobu, używa go. Jeśli zasób nie zostanie znaleziona, kontynuuje wyszukiwanie.  
  
7.  Środowisko uruchomieniowe obok kwerendy Instalatora Windows, aby ustalić, czy zestawu satelickiego nadrzędny ma zostać zainstalowany na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw, a na koniec przeszukuje go lub żądany zasób. Jeśli znajdzie zasobu w zestawie używa go. Jeśli zasób nie zostanie znaleziona, kontynuuje wyszukiwanie.  
  
8.  Środowisko wykonawcze zgłasza <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można znaleźć odpowiedni zasób rezerwowy. Jeśli wybierzesz obsłużyć zdarzenie, obsługi zdarzenia może zwrócić odwołanie do zestawu satelickiego, którego zasoby będzie służyć do wyszukiwania. W przeciwnym razie zwraca program obsługi zdarzeń `null` i wyszukiwanie jest kontynuowane.  
  
9. Wyszukuje następny środowiska uruchomieniowego nadrzędnego zestawów, tak jak poprzednie trzy kroki przy użyciu wielu potencjalnych poziomów. Każda kultura ma tylko jedną jednostkę nadrzędną, która jest zdefiniowana przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwości, ale element nadrzędny może mieć własną nadrzędnej. Wyszukaj nadrzędnego kulturami zatrzymuje się podczas kultury <xref:System.Globalization.CultureInfo.Parent%2A> właściwość zwraca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; na zasób rezerwowy Niezmienna kultura nie jest uważany za kultury nadrzędnej lub kultury, które mogą istnieć zasoby.  
  
10. Jeśli nadal nie można odnaleźć zasobu został przeszukane kultury, który pierwotnie został określony i wszystkich elementów nadrzędnych, zasobów dla kultury domyślnej (rezerwowego) jest używany. Zazwyczaj zasobów dla kultury domyślnej znajdują się w zestawie aplikacji głównej. Jednakże, można określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> właściwość <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu, aby wskazać, że ultimate lokalizacji rezerwowej dla zasobów zestawu satelickiego zamiast zestawu głównego.  
  
    > [!NOTE]
    >  Zasób domyślny jest tylko zasób, który może być skompilowana przy użyciu zestawu głównego. Chyba że określisz zestawu satelickiego przy użyciu <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu jest ostateczny powrót (końcowy element nadrzędny). Dlatego zaleca się zawsze zawierać domyślny zestaw zasobów w swoim zestawie głównym. Pozwala to zapobiec wyjątki od zgłaszane. Przez dołączenie zasobu domyślnego, pliku, który zapewnia rezerwowe dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób jest zawsze istnieje dla użytkownika, nawet jeśli nie jest kulturalnie określonych.
  
11. Na koniec, jeśli środowisko wykonawcze nie znajduje się zasób dla domyślnej kultury (rezerwowego) <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException> jest zgłaszany wyjątek, aby wskazać, że nie można odnaleźć zasobu.  
  
 Załóżmy na przykład żądania aplikacji zasobu zlokalizowane dla hiszpański (Meksyk) ( `es-MX` kultury). Środowisko uruchomieniowe najpierw szuka globalnej pamięci podręcznej zestawu, który odpowiada `es-MX`, ale nie można go odnaleźć. Środowisko uruchomieniowe wyszukuje katalog zawierający obecnie wykonywany zestaw dla `es-MX` katalogu. Jeśli nie, środowisko uruchomieniowe wyszukuje global assembly cache ponownie zestawu nadrzędnego, który odzwierciedla odpowiednie kultury rezerwowej — w tym przypadku `es` (hiszpański). Jeżeli zestaw nadrzędnego nie zostanie znaleziony, środowisko uruchomieniowe wyszukuje wszystkie potencjalne poziomy zestawów nadrzędnego dla `es-MX` kulturze, aż do znalezienia odpowiedniego zasobu. Jeśli zasób nie zostanie znaleziona, środowisko uruchomieniowe używa zasobów dla kultury domyślnej.
  
<a name="Optimizing"></a>   
#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optymalizowanie procesu bazowego zasobu .NET Framework
 W następujących warunkach można zoptymalizować ten proces, za pomocą której środowisko uruchomieniowe wyszukuje zasobów w zestawach satelickich  
  
-   Zestawy satelickie są wdrażane w tej samej lokalizacji co zestaw kodu. Jeśli zainstalowano zestaw kodu w [Global Assembly Cache](../../../docs/framework/app-domains/gac.md), zestawy satelickie są również zainstalowane w globalnej pamięci podręcznej. Jeśli zestaw kodu jest zainstalowana w katalogu, zestawy satelickie są instalowane w folderach specyficzne dla kultury tego katalogu.  
  
-   Nie zainstalowano zestawów satelickich na żądanie.  
  
-   Kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
 Optymalizowanie sondy dla zestawów satelickich, umieszczając [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) elementu i ustawienie jej `enabled` atrybutu `true` w pliku konfiguracyjnym aplikacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 Zoptymalizowane sondy dla zestawów satelickich to funkcja opcjonalna. Oznacza to, że środowisko uruchomieniowe następujące kroki opisane w temacie [proces bazowy zasobu](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) chyba że [ \<relativebindforresources — >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) element znajduje się w konfiguracji aplikacji plik i jego `enabled` ma ustawioną wartość atrybutu `true`. Jeśli jest to możliwe, proces badania zestawu satelickiego zmienia się w następujący sposób:  
  
-   Środowisko wykonawcze używa lokalizacji zestawu kodu nadrzędnego sondowania dla zestawu satelickiego. Jeśli zestaw nadrzędnego jest zainstalowany w globalnej pamięci podręcznej, środowisko uruchomieniowe sondy w pamięci podręcznej, ale nie w katalogu aplikacji. Jeśli zestaw nadrzędnego jest instalowany w katalogu aplikacji, środowisko uruchomieniowe sondy w katalogu aplikacji, ale nie w globalnej pamięci podręcznej.  
  
-   Środowisko wykonawcze nie kwerendy Instalatora Windows do instalowania zestawów satelickich na żądanie.  
  
-   W przypadku niepowodzenia sondowania dla zestawu określonego zasobu środowiska uruchomieniowego nie zgłaszała <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  

### <a name="net-core-resource-fallback-process"></a>Proces bazowy zasobu .NET core
 Proces bazowy zasobu .NET Core obejmuje następujące czynności:

1.  Środowisko uruchomieniowe podejmie próbę załadowania zestawu satelickiego dla kultury żądanej.
     * Sprawdza, czy katalog zawierający obecnie wykonywany zestaw dla podkatalogu, który odpowiada żądaną kulturę. Jeśli znajdzie podkatalogu, wyszukuje tym podkatalogu zestaw prawidłowego satelity dla żądanego kultury i ładuje je.

       > [!NOTE]
       >  W systemach operacyjnych z systemami plików sensistive przypadek (oznacza to, Linux i macOS) kultury nazwy podkatalogu wyszukiwania jest uwzględniana wielkość liter.  Nazwę podkatalogu muszą dokładnie odpowiadać wielkości liter <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (na przykład `es` lub `es-MX`).

       > [!NOTE]
       > Jeśli programista ma pochodne kontekstu ładowania zestawów niestandardowych z <xref:System.Runtime.Loader.AssemblyLoadContext>, ta sytuacja jest skomplikowane.  Jeśli wykonywanie zestaw został załadowany w kontekście niestandardowych, środowisko uruchomieniowe ładuje zestawu satelickiego do niestandardowych kontekstu.  Szczegółowe informacje wykraczają poza zakres tego dokumentu.  Zobacz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     * Jeśli złożyć Satelita nie została znaleziona, <xref:System.Runtime.Loader.AssemblyLoadContext> zgłasza <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można odnaleźć zestawu satelickiego. Jeśli wybierzesz obsłużyć zdarzenie, obsługi zdarzenia można załadować i zwrócić odwołanie do zestawu satelickiego.
     * Jeśli zestawu satelickiego nadal nie została znaleziona, AssemblyLoadContext powoduje elementu AppDomain w celu wyzwolenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można odnaleźć zestawu satelickiego. Jeśli wybierzesz obsłużyć zdarzenie, obsługi zdarzenia można załadować i zwrócić odwołanie do zestawu satelickiego.

2. Jeśli zostanie znaleziony zestawu satelickiego, środowisko uruchomieniowe wyszukuje dla żądanego zasobu. Jeśli znajdzie zasobu w zestawie używa go. Jeśli zasób nie zostanie znaleziona, kontynuuje wyszukiwanie.

     > [!NOTE]
     >  Można znaleźć zasobu w zestawie satelickim, środowisko uruchomieniowe szuka pliku zasobów, żądane przez <xref:System.Resources.ResourceManager> dla bieżącego <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.  W zasobie pliku go seaches nazwa żądanego zasobu.  Jeśli albo nie zostanie znaleziony, zasób jest traktowana jako nie można odnaleźć.

3. Środowisko uruchomieniowe wyszukuje obok zestawów kultury nadrzędnej przy użyciu wielu potencjalnych poziomów, każdorazowo, powtarzając kroki 1 i 2.

     Kultura nadrzędna jest zdefiniowany jako odpowiednie kultury rezerwowej. Ponieważ warunkiem, że dowolny zasób jest zostanie zgłoszony wyjątek, należy wziąć pod uwagę elementów nadrzędnych, podczas tworzenia rezerwowego. Ten proces umożliwia do ponownego użycia zasobów. Określony zasób na poziomie nadrzędnym powinny obejmować tylko wtedy, gdy kultury podrzędnych nie trzeba lokalizować żądanego zasobu. Na przykład, jeśli użytkownik poda zestawów satelickich dla `en` (neutralny język angielski) `en-GB` (w języku angielskim jak używany w Wielkiej Brytanii), a `en-US` (w języku angielskim jak używany w Stanach Zjednoczonych), `en` satelitarnej zawiera typowe terminologii i `en-GB` i `en-US` satelity zapewnia zastąpień dla tych warunków, które różnią się.

     Każda kultura ma tylko jedną jednostkę nadrzędną, która jest zdefiniowana przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwości, ale element nadrzędny może mieć własną nadrzędnej. Wyszukaj nadrzędnego kulturami zatrzymuje się podczas kultury <xref:System.Globalization.CultureInfo.Parent%2A> właściwość zwraca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Zasoby rezerwowe Niezmienna kultura nie uznaje się kultury nadrzędnej lub kultury, które mogą istnieć zasoby.

4. Jeśli nadal nie można odnaleźć zasobu został przeszukane kultury, który pierwotnie został określony i wszystkich elementów nadrzędnych, zasobów dla kultury domyślnej (rezerwowego) jest używany. Zazwyczaj zasobów dla kultury domyślnej znajdują się w zestawie aplikacji głównej. Jednakże, można określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> właściwość, aby wskazać, że ultimate lokalizacji rezerwowej dla zasobów zestawu satelickiego zamiast zestawu głównego.

    > [!NOTE]
    >  Zasób domyślny jest tylko zasób, który może być skompilowana przy użyciu zestawu głównego. Chyba że określisz zestawu satelickiego przy użyciu <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu jest ostateczny powrót (końcowy element nadrzędny). Dlatego zaleca się zawsze zawierać domyślny zestaw zasobów w swoim zestawie głównym. Pozwala to zapobiec wyjątki od zgłaszane. Umieszczając domyślnego pliku zasobów, podaj rezerwowe dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób zawsze jest obecny dla użytkownika, nawet jeśli nie jest kulturalnie określone.

5. Na koniec, jeśli środowisko wykonawcze nie znajdzie plik zasobów dla domyślnej kultury (rezerwowego) <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException> jest zgłaszany wyjątek, aby wskazać, że nie można odnaleźć zasobu.  Jeśli zostanie znaleziony plik zasobów, ale nie ma żądanego zasobu żądania zwraca `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ostateczny powrót do zestawu satelickiego  
 Opcjonalnie można usunąć zasoby z głównego zestawu i określ, czy środowisko uruchomieniowe powinny zostać załadowane nastąpiło przejście do zasobów z zestawem satelickim, który odpowiada określonej kultury. Aby kontrolować proces rezerwowy, należy użyć <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> Konstruktor i podać wartość <xref:System.Resources.UltimateResourceFallbackLocation> parametr, który określa, czy Menedżera zasobów należy wyodrębnić zasoby rezerwowe z głównym zestawie lub zestawie satelickim.  
  
 W poniższym przykładzie .NET Framework używa <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu, aby przechowywać zasoby rezerwowe aplikacji w zestawie satelickim francuski (`fr`) języka.  Przykład ma dwa pliki zasobów w formacie tekstowym, definiujące zasób w postaci pojedynczego ciągu o nazwie `Greeting`. Po pierwsze, resources.fr.txt, zawiera zasób języka francuskiego.
  
```  
Greeting=Bon jour!  
```  
  
 Drugi, resources,ru.txt, zawiera zasób języka rosyjskiego.  
  
```  
Greeting=Добрый день  
```  
  
 Te dwa pliki są kompilowane do plików Resources, uruchamiając [generator plików zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) z wiersza polecenia.  Zasoby języka francuskiego polecenie to:  
  
 **resgen.exe resources.fr.txt**  
  
 Zasoby języka rosyjskiego polecenie to:  
  
 **resgen.exe resources.ru.txt**  
  
 Pliki Resources są osadzone w bibliotekach dołączanych dynamicznie, uruchamiając [konsolidator zestawów (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) polecenia wiersza dla zasobu języka francuskiego w następujący sposób:  
  
 **al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 i zasobu języka rosyjskiego w następujący sposób:  
  
 **al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 Kod źródłowy aplikacji znajduje się w pliku o nazwie Example1.cs lub Example1.vb. Zawiera ona <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu, aby wskazać, że domyślny zasób aplikacji znajduje się w podkatalogu fr. Tworzy wystąpienie usługi Resource Manager, pobiera wartość `Greeting` zasobu i wyświetla go w konsoli.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Następnie można skompilować kod źródłowy języka C# z wiersza polecenia w następujący sposób:  
  
```console 
csc Example1.cs
```
  
 Polecenia dla kompilatora języka Visual Basic jest bardzo podobne:  
  
```console
vbc Example1.vb
```  
  
 Ponieważ nie istnieją żadne zasoby osadzone w głównym zestawie, nie masz można skompilować przy użyciu `/resource` przełącznika.  
  
 Po uruchomieniu tego przykładu z systemu, w której język jest inna niż rosyjski wyświetla następujące dane wyjściowe:  
  
```  
Bon jour!  
```  
## <a name="suggested-packaging-alternative"></a>Sugerowane alternatywne opakowanie  
 Ograniczenia czasu i budżetu może uniemożliwić tworzenie zestaw zasobów do każdej przeszczepiania, którą obsługuje aplikacja. Zamiast tego można utworzyć zestawu satelickiego pojedynczej kultury nadrzędnej, czy wszystkie powiązane podhodowli może użyć. Można na przykład można podać jako pojedynczy angielskiej satelicki (en) pobierany przez użytkowników, którzy żądają specyficzne dla regionu angielski zasobów i zestawem pojedynczego satelickim niemiecki (de) dla użytkowników, którzy żądają niemieckiego zasoby specyficzne dla regionu. Na przykład żądania dla języka niemieckiego jak używany w Niemczech (de-DE), Austria (de-AT), a także Szwajcarii (de-CH) może spowodować powrót do zestawu satelickiego niemiecki (de). Domyślne zasoby są końcowego rezerwowe, powinien być zasoby, które będzie wymagane przez większość użytkowników aplikacji, więc wybrać dokładnie te zasoby. Ta metoda służy do wdrażania zasobów, które są mniej kulturalnie określonych, ale mogą znacznie zmniejszyć koszty lokalizacja Twojej aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
