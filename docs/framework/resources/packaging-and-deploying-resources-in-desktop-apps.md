---
title: Pakowanie i wdrażanie zasobów w aplikacjach platformy .NET
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
ms.openlocfilehash: d64e3b5201e34541fdafa5724b0c7e8c3f6c0c0d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243053"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Pakowanie i wdrażanie zasobów w aplikacjach platformy .NET

Aplikacje polegają na programie .NET Framework <xref:System.Resources.ResourceManager> Resource Manager, reprezentowanym przez klasę, w celu pobrania zlokalizowanych zasobów. Menedżer zasobów zakłada, że model koncentratora i szprychy jest używany do pakowania i wdrażania zasobów. Centrum jest głównym zestawem, który zawiera niezlokalizowany kod wykonywalny i zasoby dla pojedynczej kultury, o nazwie kultury neutralnej lub domyślnej. Kultury domyślnej jest kultury rezerwowej dla aplikacji; jest to kultura, której zasoby są używane, jeśli nie można odnaleźć zlokalizowanych zasobów. Każda szprycha łączy się z zestawem satelickiego, który zawiera zasoby dla pojedynczej kultury, ale nie zawiera żadnego kodu.

Istnieje kilka zalet tego modelu:

- Po wdrożeniu aplikacji można stopniowo dodawać zasoby dla nowych kultur. Ponieważ późniejsze rozwijanie zasobów specyficznych dla kultury może wymagać znacznej ilości czasu, umożliwia to najpierw zwolnić aplikację główną i dostarczyć zasoby specyficzne dla kultury w późniejszym terminie.
- Można aktualizować i zmieniać zestawy satelickie aplikacji bez ponownej kompilacji aplikacji.
- Aplikacja musi załadować tylko te zestawy satelityczne, które zawierają zasoby potrzebne dla określonej kultury. Może to znacznie zmniejszyć wykorzystanie zasobów systemowych.

 Istnieją jednak również wady tego modelu:

- Należy zarządzać wieloma zestawami zasobów.
- Początkowy koszt testowania aplikacji wzrasta, ponieważ należy przetestować kilka konfiguracji. Należy pamiętać, że w dłuższej perspektywie będzie łatwiej i mniej kosztowne, aby przetestować jedną podstawową aplikację z kilku satelitów, niż do testowania i utrzymania kilku równoległych wersji międzynarodowych.

## <a name="resource-naming-conventions"></a>Konwencje nazewnictwa zasobów

Podczas pakowania zasobów aplikacji, należy nazwać je przy użyciu konwencji nazewnictwa zasobów, które oczekuje środowiska wykonawczego języka wspólnego. Środowisko wykonawcze identyfikuje zasób według jego nazwy kultury. Każdej kulturze nadano unikatową nazwę, która jest zwykle kombinacją dwuliterowej, małych nazw kultury skojarzonej z językiem i, w razie potrzeby, dwuliterowej, pisanej, najwyższej nazwy subkultury skojarzonej z krajem lub regionem. Nazwa subkultury jest zgodna z nazwą kultury, oddzieloną kreską (-). Przykłady obejmują ja-JP dla języka japońskiego, jak mówi się w Japonii, en-US dla języka angielskiego, jak mówi się w Stanach Zjednoczonych, de-DE dla języka niemieckiego, jak mówi się w Niemczech, lub de-AT dla języka niemieckiego, jak mówi się w Austrii. Zobacz kolumnę **Tag języka** na liście [nazw języków/regionów obsługiwanych przez system Windows](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c). Nazwy kultur są zgodne ze standardem zdefiniowanym przez [BCP 47](https://tools.ietf.org/html/bcp47).

> [!NOTE]
> Istnieją pewne wyjątki dla nazw kultury dwuliterowej, takich jak `zh-Hans` chiński (uproszczony).

> [!NOTE]
> Aby uzyskać informacje dotyczące tworzenia plików zasobów, zobacz [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md) i tworzenie [zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Proces bazowy zasobu

Model koncentratora i szprychy do pakowania i wdrażania zasobów używa procesu awaryjnego w celu zlokalizowania odpowiednich zasobów. Jeśli aplikacja żąda zlokalizowanego zasobu, który jest niedostępny, środowisko uruchomieniowe języka wspólnego przeszukuje hierarchię kultur dla odpowiedniego zasobu rezerwowego, który najbardziej odpowiada żądaniu aplikacji użytkownika i zgłasza wyjątek tylko w ostateczności. Na każdym poziomie hierarchii, jeśli zostanie znaleziony odpowiedni zasób, środowisko wykonawcze używa go. Jeśli zasób nie zostanie znaleziony, wyszukiwanie będzie kontynuowane na następnym poziomie.

Aby zwiększyć wydajność wyszukiwania, <xref:System.Resources.NeutralResourcesLanguageAttribute> zastosuj atrybut do głównego zestawu i przekaż go nazwę języka neutralnego, który będzie działać z głównym zestawem.

### <a name="net-framework-resource-fallback-process"></a>Proces awaryjny zasobów programu .NET Framework

Proces rezerwy zasobu platformy .NET Framework obejmuje następujące kroki:

> [!TIP]
> Można użyć [ \<relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) element konfiguracji w celu optymalizacji procesu rezerwowego zasobów i procesu, w którym sondy środowiska wykonawczego dla zestawów zasobów. Aby uzyskać więcej informacji, zobacz [optymalizacji procesu awaryjnego zasobów](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) sekcji.

1. Środowisko wykonawcze najpierw sprawdza [globalnej pamięci podręcznej zestawu](../app-domains/gac.md) dla zestawu, który pasuje do żądanej kultury dla aplikacji.

     Globalna pamięć podręczna zestawów może przechowywać zestawy zasobów, które są współużytkowane przez wiele aplikacji. Zwalnia to z konieczności dołączania określonych zestawów zasobów do struktury katalogów każdej utworzonej aplikacji. Jeśli środowisko wykonawcze znajdzie odwołanie do zestawu, przeszukuje zestaw dla żądanego zasobu. Jeśli znajdzie wpis w zestawie, używa żądanego zasobu. Jeśli nie znajdzie wpisu, kontynuuje wyszukiwanie.

2. Środowisko uruchomieniowe następnie sprawdza katalog aktualnie wykonywanego zestawu dla podkatalogu, który pasuje do żądanej kultury. Jeśli znajdzie podkatalog, przeszukuje ten podkatalog dla prawidłowego zestawu satelickiego dla żądanej kultury. Środowisko wykonawcze następnie przeszukuje zestaw satelickiego żądanego zasobu. Jeśli znajdzie zasób w zestawie, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

3. Środowisko wykonawcze następnie wysyła zapytanie do Instalatora Windows, aby ustalić, czy zestaw satelickiego ma być zainstalowany na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw i przeszukuje go lub żądany zasób. Jeśli znajdzie zasób w zestawie, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

4. Środowisko wykonawcze wywołuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może zwrócić odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie `null` program obsługi zdarzeń zwraca i wyszukiwanie jest kontynuowane.

5. Środowisko uruchomieniowe ponownie przeszukuje globalną pamięć podręczną zestawu, tym razem dla zestawu nadrzędnego żądanej kultury. Jeśli zestaw nadrzędny istnieje w globalnej pamięci podręcznej zestawów, środowisko wykonawcze przeszukuje zestaw żądanego zasobu.

     Kultury nadrzędnej jest zdefiniowany jako kultury rezerwowej odpowiednie. Należy wziąć pod uwagę rodziców jako rezerwowych kandydatów, ponieważ zapewnienie dowolnego zasobu jest lepsze niż zgłaszanie wyjątku. Ten proces umożliwia również ponowne użycie zasobów. Należy dołączyć określonego zasobu na poziomie nadrzędnym tylko wtedy, gdy kultury podrzędnej nie trzeba lokalizować żądanego zasobu. Na przykład jeśli dostarczasz zestawy `en` satelitarne `en-GB` dla (neutralny angielski), (angielski używany w Wielkiej `en-US` Brytanii) `en` i (angielski używany w `en-GB` Stanach Zjednoczonych), satelita będzie zawierać wspólną terminologię, a satelity i `en-US` satelity mogą zapewnić zastąpienia tylko tych terminów, które różnią się.

6. Następnie środowisko uruchomieniowe sprawdza katalog aktualnie wykonywanego zestawu, aby sprawdzić, czy zawiera katalog nadrzędny. Jeśli katalog nadrzędny istnieje, środowisko wykonawcze przeszukuje katalog dla prawidłowego zestawu satelickiego dla kultury nadrzędnej. Jeśli znajdzie zestaw, środowisko wykonawcze przeszukuje zestaw żądanego zasobu. Jeśli znajdzie zasób, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

7. Środowisko wykonawcze następnie wysyła zapytanie do Instalatora Windows, aby ustalić, czy nadrzędny zestaw satelickiego ma być zainstalowany na żądanie. Jeśli tak, obsługuje instalację, ładuje zestaw i przeszukuje go lub żądany zasób. Jeśli znajdzie zasób w zestawie, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

8. Środowisko wykonawcze wywołuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można znaleźć odpowiedniego zasobu rezerwowego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń może zwrócić odwołanie do zestawu satelickiego, którego zasoby będą używane do wyszukiwania. W przeciwnym razie `null` program obsługi zdarzeń zwraca i wyszukiwanie jest kontynuowane.

9. Środowisko uruchomieniowe następnego przeszukuje zestawy nadrzędne, podobnie jak w poprzednich trzech krokach, za pośrednictwem wielu potencjalnych poziomów. Każda kultura ma tylko jeden element <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadrzędny, który jest zdefiniowany przez właściwość, ale element nadrzędny może mieć własny element nadrzędny. Wyszukiwanie kultur nadrzędnych zatrzymuje się, <xref:System.Globalization.CultureInfo.Parent%2A> gdy <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>właściwość kultury zwraca; dla rezerwy zasobów kultury niezmienne nie jest uważany za kultury nadrzędnej lub kultury, które mogą mieć zasoby.

10. Jeśli kultura, która została pierwotnie określona i wszystkie rodzice zostały przeszukane, a zasób nadal nie zostanie znaleziony, używany jest zasób dla kultury domyślnej (rezerwowej). Zazwyczaj zasoby dla kultury domyślnej są uwzględniane w głównym zestawie aplikacji. Można jednak określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> właściwości <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> atrybutu, <xref:System.Resources.NeutralResourcesLanguageAttribute> aby wskazać, że ostateczną lokalizacją rezerwową dla zasobów jest zestaw satelicki, a nie główny zestaw.

    > [!NOTE]
    > Zasób domyślny jest jedynym zasobem, który można skompilować z zespołem głównym. O ile nie określisz <xref:System.Resources.NeutralResourcesLanguageAttribute> zestawu satelickiego przy użyciu atrybutu, jest to ostateczny rezerwowy (końcowy element nadrzędny). W związku z tym zaleca się, aby zawsze zawierać domyślny zestaw zasobów w zestawie głównym. Pomaga to zapobiec zgłaszaniu wyjątków. Dołączając domyślny zasób, plik zapewnia rezerwowy dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny kulturowo.

11. Na koniec, jeśli środowisko wykonawcze nie znajdzie zasobu dla domyślnej <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> kultury (rezerwowej), zgłaszany jest wyjątek lub wyjątek wskazujący, że nie można odnaleźć zasobu.

Załóżmy na przykład, że aplikacja żąda zasobu `es-MX` zlokalizowanego dla języka hiszpańskiego (Meksyk) (kultury). Środowisko wykonawcze najpierw przeszukuje globalną `es-MX`pamięć podręczną zestawu dla zestawu, który pasuje, ale nie znajduje go. Środowisko wykonawcze następnie przeszukuje katalog aktualnie wykonywanego zestawu dla `es-MX` katalogu. W przeciwnym razie środowisko wykonawcze ponownie przeszukuje globalną pamięć podręczną zestawów w `es` poszukiwaniu zestawu nadrzędnego, który odzwierciedla odpowiednią kulturę rezerwową — w tym przypadku (hiszpański). Jeśli zestaw nadrzędny nie zostanie znaleziony, środowisko wykonawcze przeszukuje wszystkie potencjalne poziomy zestawów nadrzędnych dla `es-MX` kultury, dopóki nie znajdzie odpowiedniego zasobu. Jeśli zasób nie zostanie znaleziony, środowisko wykonawcze używa zasobu dla kultury domyślnej.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optymalizacja procesu awaryjnego zasobu programu .NET Framework

W następujących warunkach można zoptymalizować proces wyszukiwania zasobów w zestawach satelickich

- Zestawy satelitarne są wdrażane w tej samej lokalizacji co zestaw kodu. Jeśli zestaw kodu jest zainstalowany w [globalnej pamięci podręcznej zestawów,](../app-domains/gac.md)zestawy satelitowane są również instalowane w globalnej pamięci podręcznej zestawów. Jeśli zestaw kodu jest zainstalowany w katalogu, zestawy satelickiego są instalowane w folderach specyficznych dla kultury tego katalogu.

- Zestawy satelitarne nie są instalowane na żądanie.

- Kod aplikacji nie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> obsługuje zdarzenia.

Optymalizacja sondy dla zestawów satelitowych przez [ \<dołączenie relativeBindForResources](../configure-apps/file-schema/runtime/relativebindforresources-element.md)>`true` element i ustawienie jego `enabled` atrybutu w pliku konfiguracji aplikacji, jak pokazano w poniższym przykładzie.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Zoptymalizowana sonda dla zestawów satelitarnych jest funkcją opt-in. Oznacza to, że środowisko wykonawcze następuje kroki opisane w [Proces rezerwowy zasobów,](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) chyba że [ \<relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) element jest obecny w pliku konfiguracyjnym aplikacji i jego `enabled` atrybut jest ustawiony na `true`. W takim przypadku proces sondowania dla zespołu satelickiego jest modyfikowany w następujący sposób:

- Środowisko wykonawcze używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego. Jeśli zestaw nadrzędny jest zainstalowany w globalnej pamięci podręcznej zestawów, sondy środowiska wykonawczego w pamięci podręcznej, ale nie w katalogu aplikacji. Jeśli zestaw nadrzędny jest zainstalowany w katalogu aplikacji, sondy środowiska wykonawczego w katalogu aplikacji, ale nie w globalnej pamięci podręcznej zestawów.

- Środowisko wykonawcze nie wysyła zapytania do Instalatora Windows w celu instalacji na żądanie zestawów satelickich.

- Jeśli sonda dla określonego zestawu zasobów nie powiedzie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> się, środowisko wykonawcze nie wywołuje zdarzenia.

### <a name="net-core-resource-fallback-process"></a>Proces awaryjny zasobu .NET Core

Proces rezerwy zasobu .NET Core obejmuje następujące kroki:

1. Środowisko wykonawcze próbuje załadować zestaw satelickiego dla żądanej kultury.
     - Sprawdza katalog aktualnie wykonywanego zestawu dla podkatalogu, który pasuje do żądanej kultury. Jeśli znajdzie podkatalog, przeszukuje ten podkatalog dla prawidłowego zestawu satelickiego dla żądanej kultury i ładuje go.

       > [!NOTE]
       > W systemach operacyjnych z systemami plików z uwzględnieniem wielkości liter (czyli Linux i macOS) wyszukiwanie podkatalogu nazwy kultury jest rozróżniane. Nazwa podkatalogu musi być dokładnie <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> zgodna z `es` `es-MX`przypadkiem (na przykład lub ).

       > [!NOTE]
       > Jeśli programista wyprowadził niestandardowy kontekst <xref:System.Runtime.Loader.AssemblyLoadContext>obciążenia zestawu z , sytuacja jest skomplikowana. Jeśli zestaw wykonujący został załadowany do kontekstu niestandardowego, środowisko wykonawcze ładuje zestaw satelickiego w kontekście niestandardowym. Szczegóły są poza zakresem dla tego dokumentu. Zobacz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Jeśli nie znaleziono zestawu satelickiego, <xref:System.Runtime.Loader.AssemblyLoadContext> wywołuje <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie jest w stanie znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń można załadować i zwrócić odwołanie do zestawu satelickiego.
     - Jeśli zestaw satelickiego nadal nie został znaleziony, AssemblyLoadContext powoduje, że AppDomain wyzwolić <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby wskazać, że nie można znaleźć zestawu satelickiego. Jeśli zdecydujesz się obsłużyć zdarzenie, program obsługi zdarzeń można załadować i zwrócić odwołanie do zestawu satelickiego.

2. Jeśli zostanie znaleziony zestaw satelickiego, środowisko wykonawcze przeszukuje go dla żądanego zasobu. Jeśli znajdzie zasób w zestawie, używa go. Jeśli nie znajdzie zasobu, kontynuuje wyszukiwanie.

     > [!NOTE]
     > Aby znaleźć zasób w zestawie satelicie, środowisko wykonawcze <xref:System.Resources.ResourceManager> wyszukuje plik zasobu żądany przez bieżący <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>plik . W pliku zasobu wyszukuje żądaną nazwę zasobu. Jeśli którykolwiek nie zostanie znaleziony, zasób jest traktowany jako nie znaleziono.

3. Środowisko uruchomieniowe następnie przeszukuje nadrzędnych zestawów kultury za pomocą wielu potencjalnych poziomów, za każdym razem powtarzając kroki 1 & 2.

     Kultury nadrzędnej jest zdefiniowany jako kultury rezerwowej odpowiednie. Należy wziąć pod uwagę rodziców jako rezerwowych kandydatów, ponieważ zapewnienie dowolnego zasobu jest lepsze niż zgłaszanie wyjątku. Ten proces umożliwia również ponowne użycie zasobów. Należy dołączyć określonego zasobu na poziomie nadrzędnym tylko wtedy, gdy kultury podrzędnej nie trzeba lokalizować żądanego zasobu. Na przykład jeśli dostarczasz zestawy `en` satelitarne `en-GB` dla (neutralny angielski), (angielski używany w Wielkiej `en-US` Brytanii) `en` i (angielski używany w `en-GB` `en-US` Stanach Zjednoczonych), satelita zawiera wspólną terminologię, a satelity i satelity zapewniają zastąpienia tylko tych terminów, które różnią się.

     Każda kultura ma tylko jeden element <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadrzędny, który jest zdefiniowany przez właściwość, ale element nadrzędny może mieć własny element nadrzędny. Wyszukiwanie kultur nadrzędnych zatrzymuje się, <xref:System.Globalization.CultureInfo.Parent%2A> gdy <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>właściwość kultury zwraca . W przypadku rezerwowego zasobu niezmienna kultura nie jest uważana za kulturę nadrzędną ani kulturę, która może mieć zasoby.

4. Jeśli kultura, która została pierwotnie określona i wszystkie rodzice zostały przeszukane, a zasób nadal nie zostanie znaleziony, używany jest zasób dla kultury domyślnej (rezerwowej). Zazwyczaj zasoby dla kultury domyślnej są uwzględniane w głównym zestawie aplikacji. Można jednak określić wartość <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> dla <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> właściwości, aby wskazać, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelickiego, a nie głównym złożeniem.

    > [!NOTE]
    > Zasób domyślny jest jedynym zasobem, który można skompilować z zespołem głównym. O ile nie określisz <xref:System.Resources.NeutralResourcesLanguageAttribute> zestawu satelickiego przy użyciu atrybutu, jest to ostateczny rezerwowy (końcowy element nadrzędny). W związku z tym zaleca się, aby zawsze zawierać domyślny zestaw zasobów w zestawie głównym. Pomaga to zapobiec zgłaszaniu wyjątków. Dołączając domyślny plik zasobu, należy podać rezerwowe dla wszystkich zasobów i upewnij się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny kulturowo.

5. Na koniec, jeśli środowisko wykonawcze nie znajdzie pliku zasobów dla domyślnej <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> kultury (rezerwowej), zostanie zgłoszony wyjątek lub wyjątek wskazujący, że nie można odnaleźć zasobu. Jeśli plik zasobu zostanie znaleziony, ale żądany `null`zasób nie jest obecny, żądanie zwraca .

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ostateczny powrót do zestawu satelickiego

Opcjonalnie można usunąć zasoby z głównego zestawu i określić, że środowisko wykonawcze należy załadować ostateczny rezerwowy zasobów z zestawu satelickiego, który odpowiada określonej kultury. Aby kontrolować proces rezerwowy, należy <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29> użyć konstruktora <xref:System.Resources.UltimateResourceFallbackLocation> i podać wartość parametru, który określa, czy Menedżer zasobów należy wyodrębnić rezerwowych zasobów z głównego zestawu lub z zestawu satelickiego.

W poniższym przykładzie .NET Framework używa atrybutu <xref:System.Resources.NeutralResourcesLanguageAttribute> do przechowywania rezerwowych zasobów aplikacji`fr`w zestawie satelicie dla języka francuskiego ( ). W przykładzie znajdują się dwa tekstowe pliki `Greeting`zasobów definiujące pojedynczy zasób o nazwie . Pierwszy, resources.fr.txt, zawiera zasób języka francuskiego.

```text
Greeting=Bon jour!
```

Drugi, resources,ru.txt, zawiera zasób języka rosyjskiego.

```text
Greeting=Добрый день
```

Te dwa pliki są kompilowane do plików .resources, uruchamiając [generator plików zasobów (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) z wiersza polecenia. W przypadku zasobu języka francuskiego polecenie jest następujące:

**resgen.exe resources.fr.txt**

Dla zasobu języka rosyjskiego polecenie jest następujące:

**resgen.exe resources.ru.txt**

Pliki .resources są osadzone w bibliotekach łączy dynamicznych przez uruchomienie [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md) z wiersza polecenia zasobu języka francuskiego w następujący sposób:

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

oraz dla zasobu języka rosyjskiego w następujący sposób:

**al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**

Kod źródłowy aplikacji znajduje się w pliku o nazwie Example1.cs lub Example1.vb. Zawiera atrybut <xref:System.Resources.NeutralResourcesLanguageAttribute> wskazujący, że domyślny zasób aplikacji znajduje się w podkatalogu fr. Tworzenie wystąpienia Menedżera zasobów, pobiera wartość zasobu `Greeting` i wyświetla go w konsoli.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Następnie można skompilować kod źródłowy języka C# z wiersza polecenia w następujący sposób:

```console
csc Example1.cs
```

Polecenie dla kompilatora języka Visual Basic jest bardzo podobne:

```console
vbc Example1.vb
```

Ponieważ nie ma żadnych zasobów osadzonych w zestawie głównym, nie `/resource` trzeba kompilować przy użyciu przełącznika.

Po uruchomieniu przykład z systemu, którego język jest inny niż rosyjski, wyświetla następujące dane wyjściowe:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Sugerowane alternatywne opakowanie

Ograniczenia czasu lub budżetu mogą uniemożliwić utworzenie zestawu zasobów dla każdej subkultury, która obsługuje aplikację. Zamiast tego można utworzyć pojedynczy zestaw satelickiego dla kultury nadrzędnej, której mogą używać wszystkie powiązane subkultury. Na przykład można podać jeden angielski zestaw satelijski (en), który jest pobierany przez użytkowników, którzy żądają zasobów w języku angielskim specyficznych dla regionu, i jeden niemiecki zestaw satelijski (de) dla użytkowników, którzy żądają zasobów niemieckich specyficznych dla regionu. Na przykład żądania dotyczące języka niemieckiego w Niemczech (de-DE), Austrii (de-AT) i Szwajcarii (de-CH) spadłyby z powrotem do niemieckiego zgromadzenia satelitarnego (de). Zasoby domyślne są ostatecznym rezerwowym i dlatego powinny być zasoby, które będą wymagane przez większość użytkowników aplikacji, więc wybierz te zasoby ostrożnie. Takie podejście wdraża zasoby, które są mniej specyficzne dla kultury, ale może znacznie zmniejszyć koszty lokalizacji aplikacji.

## <a name="see-also"></a>Zobacz też

- [Zasoby w aplikacjach klasycznych](index.md)
- [Global Assembly Cache](../app-domains/gac.md)
- [Tworzenie plików zasobów](creating-resource-files-for-desktop-apps.md)
- [Tworzenie zestawów satelickich](creating-satellite-assemblies-for-desktop-apps.md)
