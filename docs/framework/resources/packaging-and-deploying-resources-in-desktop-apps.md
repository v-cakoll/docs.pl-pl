---
title: Pakowanie i wdrażanie zasobów w aplikacjach .NET
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
ms.openlocfilehash: 9c8d459195693e8eb084f7e87427a3ea37dd63ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129929"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Pakowanie i wdrażanie zasobów w aplikacjach .NET

Aplikacje są zależne od .NET Framework Menedżer zasobów reprezentowane przez klasę <xref:System.Resources.ResourceManager> w celu pobrania zlokalizowanych zasobów. Menedżer zasobów zakłada, że model gwiazdy jest używany do pakowania i wdrażania zasobów. Koncentrator jest głównym zestawem, który zawiera Niezlokalizowany kod wykonywalny i zasoby dla pojedynczej kultury, nazywane kulturą neutralną lub domyślną. Domyślna kultura jest kulturą rezerwową dla aplikacji; jest kulturą, której zasoby są używane, jeśli nie można znaleźć zlokalizowanych zasobów. Każdy szprych nawiązuje połączenie z zestawem satelickim zawierającym zasoby dla jednej kultury, ale nie zawiera kodu.

Ten model ma kilka zalet:

- Po wdrożeniu aplikacji można stopniowo dodawać zasoby dla nowych kultur. W związku z tym, że dalsze Programowanie zasobów specyficznych dla kultury może wymagać znacznego czasu, to pozwala na pierwsze wydanie głównej aplikacji oraz dostarczanie zasobów specyficznych dla kultury w późniejszym terminie.
- Można aktualizować i zmieniać zestawy satelickie aplikacji bez konieczności ponownego kompilowania aplikacji.
- Aplikacja musi ładować tylko te zestawy satelickie, które zawierają zasoby wymagane dla określonej kultury. Może to znacznie zmniejszyć wykorzystanie zasobów systemowych.

 Jednak istnieją także wady tego modelu:

- Należy zarządzać wieloma zestawami zasobów.
- Początkowy koszt testowania aplikacji wzrasta, ponieważ należy przetestować kilka konfiguracji. Należy pamiętać, że w długim okresie będzie łatwiejsze i tańsze przetestowanie jednej podstawowej aplikacji z kilkoma satelitami, niż testowanie i obsługa kilku równoległych wersji międzynarodowych.

## <a name="resource-naming-conventions"></a>Konwencje nazewnictwa zasobów

Podczas pakowania zasobów aplikacji należy nadać im nazwy przy użyciu konwencji nazewnictwa zasobów, których oczekuje środowisko uruchomieniowe języka wspólnego. Środowisko uruchomieniowe identyfikuje zasób według jego nazwy kultury. Każda kultura ma unikatową nazwę, która zwykle jest kombinacją dwuliterowej nazwy kultury, która jest skojarzona z językiem i, w razie potrzeby, z dwuliterową nazwą podkultury Wielkiej, skojarzoną z danym krajem lub regionem. Nazwa kultury jest zgodna z nazwą kultury, oddzieloną kreską (-). Przykłady obejmują ja-JP dla języka japońskiego w Japonii, en-US dla języka angielskiego w Stany Zjednoczone, de-DE dla języka niemieckiego w Niemczech lub w odniesieniu do języka niemieckiego, który jest mówiony w Austrii. Zobacz kolumnę **tag języka** na [liście nazw języków/regionów obsługiwanych przez system Windows](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c). Nazwy kultur są zgodne ze standardem zdefiniowanym przez [BCP 47](https://tools.ietf.org/html/bcp47).

> [!NOTE]
> Istnieją pewne wyjątki dla nazw kultur dwuliterowych, takich jak `zh-Hans` for chiński (uproszczony).

> [!NOTE]
> Informacje o tworzeniu plików zasobów można znaleźć w temacie [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md) i [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Proces bazowy zasobu

Model gwiazdy do pakowania i wdrażania zasobów używa procesu rezerwowego do lokalizowania odpowiednich zasobów. Jeśli aplikacja żąda zlokalizowanego zasobu, który jest niedostępny, środowisko uruchomieniowe języka wspólnego przeszukuje hierarchię kultur dla odpowiedniego zasobu rezerwowego, który najlepiej pasuje do żądania application's użytkownika i zgłasza wyjątek tylko jako Ostatni etap. Na każdym poziomie hierarchii, jeśli zostanie znaleziony odpowiedni zasób, środowisko uruchomieniowe użyje go. Jeśli zasób nie zostanie znaleziony, wyszukiwanie będzie kontynuowane na następnym poziomie.

Aby zwiększyć wydajność wyszukiwania, zastosuj atrybut <xref:System.Resources.NeutralResourcesLanguageAttribute> do głównego zestawu i przekaż mu nazwę języka neutralnego, który będzie współdziałać z Twoim głównym zestawem.

### <a name="net-framework-resource-fallback-process"></a>Proces rezerwowy zasobów .NET Framework

Proces rezerwowy zasobów .NET Framework obejmuje następujące kroki:

> [!TIP]
> Aby zoptymalizować proces rezerwowy zasobów i proces, w którym sondy środowiska uruchomieniowego dla zestawów zasobów, może być możliwe użycie elementu konfiguracji [\<relativeBindForResources](../configure-apps/file-schema/runtime/relativebindforresources-element.md) . Aby uzyskać więcej informacji, zobacz sekcję [Optymalizacja procesu rezerwowego zasobów](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) .

1. Środowisko uruchomieniowe najpierw sprawdza [globalną pamięć podręczną zestawów](../app-domains/gac.md) dla zestawu, który jest zgodny z żądaną kulturą dla aplikacji.

     Globalna pamięć podręczna zestawów może przechowywać zestawy zasobów, które są współużytkowane przez wiele aplikacji. Pozwala to na dołączenie określonych zestawów zasobów do struktury katalogów każdej utworzonej aplikacji. Jeśli środowisko uruchomieniowe odnajdzie odwołanie do zestawu, przeszukuje zestaw dla żądanego zasobu. Jeśli odnajdzie wpis w zestawie, używa żądanego zasobu. Jeśli nie znajdzie wpisu, kontynuuje wyszukiwanie.

2. Następnie środowisko uruchomieniowe sprawdza katalog aktualnie wykonywanego zestawu dla podkatalogu, który jest zgodny z żądaną kulturą. Jeśli odnajdzie podkatalog, przeszukuje ten podkatalog dla prawidłowego zestawu satelickiego dla wymaganej kultury. Środowisko uruchomieniowe następnie przeszukuje zestaw satelicki dla żądanego zasobu. W przypadku znalezienia zasobu w zestawie zostanie on użyty. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

3. Środowisko uruchomieniowe następnym zażąda Instalator Windows, aby określić, czy zestaw satelicki ma być zainstalowany na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw i przeszukuje go lub żądany zasób. W przypadku znalezienia zasobu w zestawie zostanie on użyty. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

4. Środowisko uruchomieniowe wywołuje zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>, aby wskazać, że nie można znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może zwrócić odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie program obsługi zdarzeń zwraca `null` i wyszukiwanie będzie kontynuowane.

5. Następnie środowisko uruchomieniowe ponownie przeszukuje globalną pamięć podręczną zestawów, tym razem dla zestawu nadrzędnego żądanej kultury. Jeśli zestaw nadrzędny istnieje w globalnej pamięci podręcznej zestawów, środowisko uruchomieniowe przeszukuje zestaw dla żądanego zasobu.

     Kultura nadrzędna jest definiowana jako odpowiednia kultura rezerwowa. Rozważ użycie obiektów nadrzędnych jako kandydatów Fallback, ponieważ dostarczenie dowolnego zasobu jest preferowane do zgłaszania wyjątku. Ten proces pozwala również ponownie wykorzystać zasoby. Określony zasób powinien znajdować się na poziomie nadrzędnym tylko wtedy, gdy Kultura podrzędna nie musi lokalizować żądanego zasobu. Na przykład, jeśli dostarczasz zestawy satelickie dla `en` (neutralnego alfabetu angielskiego), `en-GB` (angielski jako mówiony w Zjednoczonym Królestwie) i `en-US` (angielski jako mówiony w Stany Zjednoczone), Satelita `en` będzie zawierać powszechną terminologię i @no __t_4_ `en-US` i satelity mogą zapewnić przesłonięcia tylko te warunki, które się różnią.

6. Następnie środowisko uruchomieniowe sprawdza katalog aktualnie wykonywanego zestawu, aby zobaczyć, czy zawiera katalog nadrzędny. Jeśli katalog nadrzędny istnieje, środowisko uruchomieniowe przeszukuje katalog pod kątem prawidłowego zestawu satelickiego dla kultury nadrzędnej. Jeśli odnajdzie zestaw, środowisko uruchomieniowe przeszukuje zestaw dla żądanego zasobu. W przypadku znalezienia zasobu zostanie on użyty. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

7. Środowisko uruchomieniowe następnym zapytaniem Instalator Windows, aby określić, czy nadrzędny zestaw satelicki ma być zainstalowany na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw i przeszukuje go lub żądany zasób. W przypadku znalezienia zasobu w zestawie zostanie on użyty. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

8. Środowisko uruchomieniowe wywołuje zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>, aby wskazać, że nie można znaleźć odpowiedniego zasobu rezerwowego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może zwrócić odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie program obsługi zdarzeń zwraca `null` i wyszukiwanie będzie kontynuowane.

9. Środowisko uruchomieniowe następnym szuka zestawów nadrzędnych, jak w poprzednich trzech krokach, za pomocą wielu potencjalnych poziomów. Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez właściwość <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>, ale element nadrzędny może mieć własny element nadrzędny. Wyszukiwanie kultur nadrzędnych jest przerywane, gdy właściwość <xref:System.Globalization.CultureInfo.Parent%2A> kultury zwraca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; w przypadku rezerwy zasobów Niezmienna kultura nie jest uważana za kulturę nadrzędną ani kulturę, która może mieć zasoby.

10. Jeśli kultura, która była pierwotnie określona i wszystkie elementy nadrzędne zostały przeszukane, a zasób nadal nie został znaleziony, używana jest wartość domyślna kultury (Fallback). Zazwyczaj zasoby dla kultury domyślnej są zawarte w głównym zestawie aplikacji. Można jednak określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> dla właściwości <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> atrybutu <xref:System.Resources.NeutralResourcesLanguageAttribute>, aby wskazać, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelity, a nie głównym zestawem.

    > [!NOTE]
    > Domyślny zasób jest jedynym zasobem, który można skompilować przy użyciu głównego zestawu. O ile nie określisz zestawu satelickiego przy użyciu atrybutu <xref:System.Resources.NeutralResourcesLanguageAttribute>, jest to ostateczna rezerwa (końcowy element nadrzędny). Dlatego zaleca się, aby zawsze zawierać domyślny zestaw zasobów w zestawie głównym. Pomaga to zapobiegać zgłaszaniu wyjątków. Przez dołączenie zasobu domyślnego, plik dostarcza rezerwę dla wszystkich zasobów i gwarantuje, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny dla kultury.

11. Na koniec Jeśli środowisko uruchomieniowe nie znajdzie zasobu dla kultury domyślnej (rezerwowej), zostanie zgłoszony wyjątek <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException>, aby wskazać, że nie można odnaleźć zasobu.

Załóżmy na przykład, że aplikacja żąda zasobu zlokalizowanego w języku hiszpańskim (Meksyk) (kultura `es-MX`). Środowisko uruchomieniowe najpierw przeszukuje globalną pamięć podręczną zestawów dla zestawu, który jest zgodny `es-MX`, ale go nie znajdzie. Środowisko uruchomieniowe następnie przeszukuje katalog aktualnie wykonywanego zestawu dla katalogu `es-MX`. Niepowodzenie oznacza, że środowisko uruchomieniowe ponownie przeszukuje globalną pamięć podręczną zestawów dla zestawu nadrzędnego, który odzwierciedla odpowiednią kulturę rezerwową — w tym przypadku `es` (hiszpański). Jeśli zestaw nadrzędny nie zostanie znaleziony, środowisko uruchomieniowe przeszukuje wszystkie potencjalne poziomy zestawów nadrzędnych dla kultury `es-MX`, dopóki nie znajdzie odpowiedniego zasobu. Jeśli zasób nie zostanie znaleziony, środowisko uruchomieniowe użyje zasobu dla kultury domyślnej.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optymalizowanie procesu rezerwowego .NET Framework zasobów

W następujących warunkach można zoptymalizować proces, za pomocą którego środowisko uruchomieniowe wyszukuje zasoby w zestawach satelickich

- Zestawy satelickie są wdrażane w tej samej lokalizacji co zestaw kodu. Jeśli zestaw kodu jest zainstalowany w [globalnej pamięci podręcznej zestawów](../app-domains/gac.md), zestawy satelickie są również zainstalowane w globalnej pamięci podręcznej zestawów. Jeśli zestaw kodu jest zainstalowany w katalogu, zestawy satelickie są instalowane w folderach specyficznych dla kultury tego katalogu.

- Zestawy satelickie nie są zainstalowane na żądanie.

- Kod aplikacji nie obsługuje zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

Możesz zoptymalizować sondę dla zestawów satelitarnych, dołączając [\<relativeBindForResources >](../configure-apps/file-schema/runtime/relativebindforresources-element.md) elementu i ustawiając jego atrybut `enabled` na `true` w pliku konfiguracyjnym aplikacji, jak pokazano w poniższym przykładzie.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Optymalizacja pod kątem zestawów satelitarnych to funkcja opcjonalna. Oznacza to, że środowisko uruchomieniowe postępuje zgodnie z krokami opisanymi w [procesie rezerwowym zasobu](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) , chyba że element [\<relativeBindForResources >](../configure-apps/file-schema/runtime/relativebindforresources-element.md) jest obecny w pliku konfiguracji aplikacji, a jego atrybut `enabled` jest ustawiony na `true`. W takim przypadku proces sondowania dla zestawu satelickiego jest modyfikowany w następujący sposób:

- Środowisko uruchomieniowe używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego. Jeśli zestaw nadrzędny jest zainstalowany w globalnej pamięci podręcznej zestawów, sondy środowiska uruchomieniowego w pamięci podręcznej, ale nie w katalogu aplikacji. Jeśli zestaw nadrzędny jest zainstalowany w katalogu aplikacji, sondy środowiska uruchomieniowego w katalogu aplikacji, ale nie w globalnej pamięci podręcznej zestawów.

- Środowisko uruchomieniowe nie wykonuje zapytania do Instalator Windows na potrzeby instalacji zestawów satelitarnych na żądanie.

- Jeśli sonda dla określonego zestawu zasobów ulegnie awarii, środowisko uruchomieniowe nie zgłosi zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

### <a name="net-core-resource-fallback-process"></a>Proces rezerwowy zasobów platformy .NET Core

Proces rezerwowy zasobów platformy .NET Core obejmuje następujące kroki:

1. Środowisko uruchomieniowe próbuje załadować zestaw satelicki dla wymaganej kultury.
     - Sprawdza katalog aktualnie wykonywanego zestawu dla podkatalogu, który jest zgodny z żądaną kulturą. Jeśli odnajdzie podkatalog, przeszukuje ten podkatalog dla prawidłowego zestawu satelickiego dla wymaganej kultury i ładuje go.

       > [!NOTE]
       > W systemach operacyjnych z systemami plików z uwzględnieniem wielkości liter (czyli Linux i macOS) Wyszukiwanie w podkatalogu nazw kultur jest rozróżniana wielkość liter. Nazwa podkatalogu musi dokładnie pasować do wielkości liter <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (na przykład `es` lub `es-MX`).

       > [!NOTE]
       > Jeśli programista poprowadził niestandardowy kontekst ładowania zestawu od <xref:System.Runtime.Loader.AssemblyLoadContext>, sytuacja jest skomplikowana. Jeśli zestaw wykonawczy został załadowany do kontekstu niestandardowego, środowisko uruchomieniowe ładuje zestaw satelicki do niestandardowego kontekstu. Szczegóły znajdują się poza zakresem tego dokumentu. Zobacz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Jeśli nie można odnaleźć asemblera satelitarnego, <xref:System.Runtime.Loader.AssemblyLoadContext> wywołuje zdarzenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>, aby wskazać, że nie można znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może załadować i zwrócić odwołanie do zestawu satelickiego.
     - Jeśli zestaw satelicki nadal nie został znaleziony, AssemblyLoadContext powoduje, że obiekt AppDomain wyzwala zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>, aby wskazać, że nie można znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może załadować i zwrócić odwołanie do zestawu satelickiego.

2. W przypadku znalezienia zestawu satelickiego środowisko uruchomieniowe przeszukuje go w poszukiwaniu żądanego zasobu. W przypadku znalezienia zasobu w zestawie zostanie on użyty. Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.

     > [!NOTE]
     > Aby znaleźć zasób w ramach zestawu satelickiego, środowisko uruchomieniowe wyszukuje plik zasobów żądany przez <xref:System.Resources.ResourceManager> dla bieżącego <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. W pliku zasobów szuka żądanej nazwy zasobu. Jeśli nie zostanie znaleziony, zasób jest traktowany jako nieodnaleziony.

3. Środowisko uruchomieniowe następnym szuka zestawów kultur nadrzędnych za pomocą wielu możliwych poziomów, za każdym razem, gdy powtarzają się kroki 1 & 2.

     Kultura nadrzędna jest definiowana jako odpowiednia kultura rezerwowa. Rozważ użycie obiektów nadrzędnych jako kandydatów Fallback, ponieważ dostarczenie dowolnego zasobu jest preferowane do zgłaszania wyjątku. Ten proces pozwala również ponownie wykorzystać zasoby. Określony zasób powinien znajdować się na poziomie nadrzędnym tylko wtedy, gdy Kultura podrzędna nie musi lokalizować żądanego zasobu. Na przykład, jeśli dostarczasz zestawy satelickie dla `en` (neutralnego alfabetu angielskiego), `en-GB` (angielski jako mówiony w Zjednoczonym Królestwie) i `en-US` (angielski jako mówiony w Stany Zjednoczone), `en` Satelita zawiera wspólną terminologię i `en-GB` `en-US` i satelity udostępniają zastąpienia tylko dla tych warunków, które się różnią.

     Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez właściwość <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType>, ale element nadrzędny może mieć własny element nadrzędny. Wyszukiwanie kultur nadrzędnych jest przerywane, gdy właściwość <xref:System.Globalization.CultureInfo.Parent%2A> kultury zwraca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. W przypadku rezerwy zasobów Niezmienna kultura nie jest uważana za kulturę nadrzędną ani kulturę, która może mieć zasoby.

4. Jeśli kultura, która była pierwotnie określona i wszystkie elementy nadrzędne zostały przeszukane, a zasób nadal nie został znaleziony, używana jest wartość domyślna kultury (Fallback). Zazwyczaj zasoby dla kultury domyślnej są zawarte w głównym zestawie aplikacji. Można jednak określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> właściwości <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A>, aby wskazać, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelity, a nie głównym zestawem.

    > [!NOTE]
    > Domyślny zasób jest jedynym zasobem, który można skompilować przy użyciu głównego zestawu. O ile nie określisz zestawu satelickiego przy użyciu atrybutu <xref:System.Resources.NeutralResourcesLanguageAttribute>, jest to ostateczna rezerwa (końcowy element nadrzędny). Dlatego zaleca się, aby zawsze zawierać domyślny zestaw zasobów w zestawie głównym. Pomaga to zapobiegać zgłaszaniu wyjątków. Dołączając domyślny plik zasobów, należy podać rezerwę dla wszystkich zasobów i upewnić się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny dla kultury.

5. Na koniec Jeśli środowisko uruchomieniowe nie odnajdzie pliku zasobów dla kultury domyślnej (rezerwowej), zostanie zgłoszony wyjątek <xref:System.Resources.MissingManifestResourceException> lub <xref:System.Resources.MissingSatelliteAssemblyException>, aby wskazać, że nie można odnaleźć zasobu. Jeśli plik zasobów zostanie znaleziony, ale żądany zasób nie jest obecny, żądanie zwróci `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ostateczny powrót do zestawu satelickiego

Opcjonalnie można usunąć zasoby z głównego zestawu i określić, że środowisko uruchomieniowe ma ładować ostateczne zasoby rezerwowe z zestawu satelitarnego, który odpowiada określonej kulturze. Aby kontrolować proces rezerwowy, należy użyć konstruktora <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> i podać wartość parametru <xref:System.Resources.UltimateResourceFallbackLocation>, który określa, czy Menedżer zasobów powinien wyodrębnić zasoby rezerwowe z zestawu głównego lub z zestawu satelickiego.

W poniższym przykładzie .NET Framework używany jest atrybut <xref:System.Resources.NeutralResourcesLanguageAttribute> do przechowywania rezerwowych zasobów aplikacji w zestawie satelitarnym dla języka francuskiego (`fr`). Przykład ma dwa pliki zasobów tekstowych, które definiują pojedynczy ciąg zasobów o nazwie `Greeting`. Pierwszy z zasobów. fr. txt zawiera zasób języka francuskiego.

```text
Greeting=Bon jour!
```

Drugi, zasoby, ru. txt, zawiera zasób języka rosyjskiego.

```text
Greeting=Добрый день
```

Te dwa pliki są kompilowane do plików Resources, uruchamiając [Generator plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) z wiersza polecenia. Dla zasobu języka francuskiego polecenie to:

**Resgen. exe Resources. fr. txt**

Dla zasobu języka rosyjskiego polecenie to:

**Resgen. exe Resources. ru. txt**

Pliki resources są osadzane w bibliotekach dołączanych dynamicznie przez uruchomienie [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) z wiersza polecenia dla zasobu języka francuskiego w następujący sposób:

**Al/t: lib/embed: Resources. fr. resources/Culture: fr/out: fr\Example1.resources.dll**

i dla zasobu języka rosyjskiego w następujący sposób:

**Al/t: lib/embed: Resources. ru. resources/Culture: ru/out: ru\Example1.resources.dll**

Kod źródłowy aplikacji znajduje się w pliku o nazwie Example1.cs lub example1. vb. Zawiera atrybut <xref:System.Resources.NeutralResourcesLanguageAttribute>, aby wskazać, że domyślny zasób aplikacji znajduje się w podkatalogu fr. Tworzy wystąpienie Menedżer zasobów, pobiera wartość zasobu `Greeting` i wyświetla go w konsoli programu.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Następnie można skompilować C# kod źródłowy z wiersza polecenia w następujący sposób:

```console
csc Example1.cs
```

Polecenie dla kompilatora Visual Basic jest bardzo podobne:

```console
vbc Example1.vb
```

Ponieważ nie ma żadnych zasobów osadzonych w zestawie głównym, nie trzeba kompilować przy użyciu przełącznika `/resource`.

Po uruchomieniu przykładu z systemu, którego język to coś innego niż rosyjski, wyświetla następujące dane wyjściowe:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Sugerowane alternatywne opakowanie

Ograniczenia czasu lub budżetu mogą uniemożliwiać utworzenie zestawu zasobów dla każdej podkultury obsługiwanej przez aplikację. Zamiast tego można utworzyć pojedynczy zestaw satelicki dla kultury nadrzędnej, którego mogą używać wszystkie powiązane podkultury. Można na przykład dostarczyć pojedynczy angielski zestaw satelicki (EN), który jest pobierany przez użytkowników, którzy żądają zasobów w języku angielskim specyficznym dla regionu, oraz jednego zestawu satelickiego dla Niemiec (de) dla użytkowników żądających zasobów niemieckich specyficznych dla regionu. Na przykład żądania dotyczące języka niemieckiego w Niemczech (de-DE), Austrii (de-AT) i Szwajcarii (de-CH) zostałyby przywrócone do niemieckiego zestawu satelickiego (de). Domyślne zasoby są końcową rezerwą i dlatego powinny być zasobami, które będą wymagane przez większość użytkowników aplikacji, dlatego należy starannie wybierać te zasoby. Takie podejście wdraża zasoby, które są mniej specyficzne dla kultury, ale znacznie zmniejsza koszty lokalizacji aplikacji.

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach klasycznych](index.md)
- [Global Assembly Cache](../app-domains/gac.md)
- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md)
