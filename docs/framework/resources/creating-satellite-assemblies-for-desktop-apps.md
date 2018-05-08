---
title: Tworzenie zestawów satelickich dla aplikacji klasycznych
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
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c308c7e16f106d00e5fd1b5ad820f8b330f4bbbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Tworzenie zestawów satelickich dla aplikacji klasycznych
Pliki zasobów odgrywają kluczową rolę w zlokalizowanych aplikacji. Umożliwiają one aplikacji do wyświetlenia ciągów, obrazy i innych danych przez użytkownika języka i kultury oraz w celu zapewnienia alternatywnych danych, jeśli zasoby dla języka dla użytkownika lub kultury są niedostępne. .NET Framework wykorzystuje model gwiazdy — Aby znaleźć i pobrać zlokalizowanych zasobów. Koncentrator jest główny zestaw zawierający kod wykonywalny niemożliwe do zlokalizowania i zasobów dla kultury pojedynczego, nazywanego zero lub domyślną kulturę. Domyślną kulturę jest kultury rezerwowej dla aplikacji; Jeśli nie są dostępne nie zlokalizowanych zasobów jest używany. Możesz użyć <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut do wyznaczenia kultura kultury domyślnej aplikacji. Każdy gwiazdy łączy zestawu satelickiego, który zawiera zasoby dla pojedynczego kultury zlokalizowany, ale nie zawiera żadnego kodu. Ponieważ zestawów satelickich nie są częścią zestawu głównego, można łatwo aktualizacji lub zastąpienia zasobów, które odpowiadają określoną kulturę bez zastępowania główny zestaw aplikacji.  
  
> [!NOTE]
>  Zasoby aplikacji domyślną kulturę również mogą być przechowywane w zestawie satelickim. Aby to zrobić, należy przypisać <xref:System.Resources.NeutralResourcesLanguageAttribute> wartość atrybutu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Nazwa zestawu satelity i lokalizację  
 Model gwiazdy wymaga, umieść zasoby w określonych lokalizacjach, dzięki czemu można je łatwo znajduje się i używane. Jeśli to zrobisz nie kompilacji i nazwy zasobów zgodnie z oczekiwaniami, lub nie należy umieszczać je w odpowiednich lokalizacjach, środowisko uruchomieniowe języka wspólnego nie będzie mógł je znaleźć i zamiast tego użyj zasobów kultury domyślnej. Menedżer zasobów .NET Framework, reprezentowany przez <xref:System.Resources.ResourceManager> obiektów, uzyskano dostęp automatycznie zlokalizowanych zasobów. Menedżer zasobów wymaga następujących elementów:  
  
-   Zestaw satelicki pojedynczego musi zawierać wszystkie zasoby dla określonej kultury. Innymi słowy należy skompilować wiele plików txt lub .resx w plik .resources binarne pojedynczego.  
  
-   Musi istnieć oddzielne podkatalogu w katalogu aplikacji dla każdej zlokalizowanych kultury przechowujący zasoby tego kultury. Nazwa podkatalogu musi być taka sama jak nazwa kultury. Alternatywnie można przechowywać ponownie zestawy satelickie w globalnej pamięci podręcznej zestawów. W takim przypadku składnik informacji kultury silna nazwa zestawu musi wskazywać jego kultury. (Zobacz [instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów](#SN) dalszej części tego tematu.)  
  
    > [!NOTE]
    >  Jeśli aplikacja zawiera zasoby podhodowli, umieść przeszczepiania każdego w osobnym podkatalogu w katalogu aplikacji. Nie umieszczaj podhodowli w podkatalogach katalogu ich głównego kultury.  
  
-   Zestawu satelickiego musi mieć taką samą nazwę jak aplikacji i muszą używać rozszerzenia nazwy pliku ". resources.dll". Na przykład jeśli aplikacja nosi nazwę Example.exe, nazwę każdego zestawu satelickiego powinna być Example.resources.dll. Uwaga satelitarne nazwy zestawu nie wskazuje kulturę jego plików zasobów. Jednak zestawu satelickiego pojawia się w katalogu, w którym określenia kultury.  
  
-   Informacje na temat kultury zestawu satelickiego muszą być zawarte w metadanych zestawu. Aby zapisać nazwę kultury w metadanych zestawu satelickiego, należy określić `/culture` opcji, gdy używasz [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) Osadzanie zasobów w zestawu satelickiego.  
  
 Na poniższej ilustracji przedstawiono przykładowe katalogu struktury i lokalizacji wymagania dotyczące aplikacji, które nie jest instalowany w [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md). Elementy z rozszerzenia .txt i .resources nie będzie składnikiem końcowe aplikacji. Są to pliki pośredniego zasobów pozwala utworzyć zestawy satelickie końcowego zasobów. W tym przykładzie można zastąpić pliki .resx dla plików txt. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Zestawy satelitarne](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Katalogu zestawów satelickich  
  
## <a name="compiling-satellite-assemblies"></a>Kompilowanie zestawów satelickich  
 Możesz użyć [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) skompilować pliki tekstowe i pliki XML (resx), które zawierają zasoby do plików binarnych .resources. Następnie należy użyć [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) skompilować .resources — pliki do zestawów satelickich. Al.exe tworzy zestaw na podstawie plików .resources, które określisz. Zestawy satelickie może zawierać tylko zasoby; nie mogą zawierać żadnego kodu wykonywalnego.  
  
 Polecenie Al.exe tworzy zestaw satelicki dla aplikacji `Example` z strings.de.resources pliku zasobów niemieckim.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Polecenie Al.exe tworzy także zestaw satelicki dla aplikacji `Example` z strings.de.resources pliku. **Template** opcja powoduje, że zestawu satelickiego dziedziczenia wszystkich metadanych zestawu z wyjątkiem informacji o kulturze z nadrzędnego zestawu (Example.dll).  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 W poniższej tabeli opisano opcje Al.exe używane w tych poleceniach bardziej szczegółowo.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-docelowych:** lib|Określa, że Twoje zestawu satelickiego jest skompilowana do pliku biblioteki (.dll). Ponieważ zestaw satelicki nie zawiera kodu wykonywalnego, a nie główny zestaw aplikacji, musisz najpierw zapisać zestawy satelickie jako biblioteki dll.|  
|**-osadzić:** strings.de.resources|Określa nazwę pliku zasobu do osadzenia kiedy Al.exe kompiluje zestawu. Wiele plików .resources można osadzić w zestawie satelickim, ale jeśli wykonujesz model gwiazdy — należy skompilować jednego zestawu satelickiego dla każdego kultury. Można jednak utworzyć oddzielne .resources — pliki do ciągów i obiektów.|  
|**-kultury:** de|Określa kulturę zasobów do skompilowania. Środowisko uruchomieniowe języka wspólnego używa tych informacji podczas wyszukiwania zasobów dla określonej kultury. Jeśli zostanie pominięta, Al.exe nadal będzie kompilować zasobu, ale środowisko uruchomieniowe nie będzie można go, gdy użytkownik zażąda go.|  
|**-out:** Example.resources.dll|Określa nazwę pliku wyjściowego. Nazwa musi występować po standard nazewnictwa *nazwę bazową*.resources. *rozszerzenie*, gdzie *nazwę bazową* jest nazwą zestawu głównego i *rozszerzenia* jest prawidłowe rozszerzenie (na przykład .dll). Należy pamiętać, że środowisko wykonawcze nie jest możliwość określenia kultury zestawu satelickiego, na podstawie jego nazwy pliku wyjściowego; należy użyć **/kultury** opcję, aby określić go.|  
|**-szablonu:** Example.dll|Określa, z którego zestawu satelickiego będzie dziedziczyć wszystkich metadanych zestawu z wyjątkiem pola kultury zestawu. Ta opcja dotyczy zestawy satelickie tylko wtedy, gdy określ zestaw, który ma [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Aby uzyskać pełną listę opcji dostępnych z Al.exe zobacz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Zestawy satelickie: Przykład  
 Poniżej przedstawiono prosty przykład "Hello world", która wyświetla komunikat zawierający zlokalizowane pozdrowienie. Przykład obejmuje zasoby angielski (Stany Zjednoczone), francuski (Francja) i kultur rosyjski (Rosji), a jego rezerwowej kultury jest angielski. Aby utworzyć w przykładzie, wykonaj następujące czynności:  
  
1.  Utwórz plik zasobu o nazwie Greeting.resx lub Greeting.txt, aby zawierała zasobów dla kultury domyślnej. Przechowywanie jednego ciągu o nazwie `HelloString` którego wartość wynosi "Witaj świecie!" w tym pliku.  
  
2.  Wskazuje, że język angielski (en) jest kultury domyślnej aplikacji, Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybutu pliku AssemblyInfo aplikacji lub pliku kodu źródłowego głównego, który zostanie skompilowany w zestawie głównym aplikacji.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Dodaj obsługę dodatkowych kultury (en US, fr-FR i ru-RU) do aplikacji w następujący sposób:  
  
    -   Do obsługi en US lub kultury angielski (Stany Zjednoczone), Utwórz plik zasobu o nazwie Greeting.en US.resx lub Greeting.en US.txt i przechowywania w nim jednego ciągu o nazwie `HelloString` którego wartość wynosi "Hi świecie!"  
  
    -   Do obsługi, fr-FR lub kultury francuski (Francja), Utwórz plik zasobu o nazwie Greeting.fr FR.resx lub Greeting.fr FR.txt i przechowywania w nim jednego ciągu o nazwie `HelloString` którego wartość wynosi "Salut w całości le monde!"  
  
    -   Do obsługi, ru-RU lub kultury rosyjski (Rosji), Utwórz plik zasobu o nazwie Greeting.ru RU.resx lub Greeting.ru RU.txt i przechowywania w nim jednego ciągu o nazwie `HelloString` którego wartość wynosi "Всем привет!"  
  
4.  Użyj [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) skompilować każdego tekstu lub plik zasobu XML w pliku .resources binarnego. Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jako pliki resx lub txt, ale z rozszerzeniem .resources. Jeśli utworzysz przykładzie z programem Visual Studio procesu kompilacji odbywa się automatycznie. Jeśli nie używasz programu Visual Studio, uruchom następujące polecenia, aby skompilować pliki .resx do plików .resources:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     Jeśli zasoby są w plikach tekstowych zamiast plików XML, Zastąp .resx rozszerzenia .txt.  
  
5.  Skompiluj następujący kod źródłowy wraz z zasobów dla kultury domyślnej w zestawie głównym aplikacji:  
  
    > [!IMPORTANT]
    >  Jeśli tworzenie w przykładzie przy użyciu wiersza polecenia, a nie programu Visual Studio, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> konstruktora klasy do następującego: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Jeśli aplikacja nosi nazwę przykład i kompilacja z wiersza polecenia, to polecenie dla kompilatora C#:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Odpowiednie polecenie kompilatora Visual Basic jest:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Utworzyć podkatalogu w katalogu głównego aplikacji dla każdego zlokalizowanych kultury obsługiwanych przez aplikację. Należy utworzyć en US, fr-FR i podkatalogu ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi jako część procesu kompilacji.  
  
7.  Osadzanie plików .resources specyficzne dla kultury poszczególnych w zestawy satelickie i zapisać je do odpowiedniego katalogu. To polecenie, aby to zrobić dla każdego pliku .resources jest:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     gdzie *kultury* to nazwa kultury, którego zestawu satelickiego zawiera zasoby. Visual Studio automatycznie obsługuje ten proces.  
  
 Następnie można uruchomić przykład. Szablon losowo wprowadzi jednym z obsługiwanych kulturami bieżącej kultury i wyświetlania zlokalizowanych powitania.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów  
 Zamiast instalowania zestawów w podkatalogu lokalnych aplikacji, można je zainstalować w globalnej pamięci podręcznej zestawów. Jest to szczególnie przydatne, jeśli masz bibliotek klas i zestawy zasobów biblioteki klasy, które są używane przez wiele aplikacji.  
  
 Instalowanie zestawów w globalnej pamięci podręcznej zestawów musi mieć one silnej nazwy. Zestawy o silnych nazwach są podpisane za pomocą prawidłowej pary kluczy publiczny/prywatny. Zawierają one informacje o wersji środowiska uruchomieniowego używa w celu określenia, które zestawu na potrzeby zrealizować żądanie powiązania. Aby uzyskać więcej informacji na temat silne nazwy i wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md). Aby uzyskać więcej informacji o silnych nazwach, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Podczas tworzenia aplikacji, jest mało prawdopodobne, że mają dostęp do końcowego pary kluczy publiczny/prywatny. Aby można było zainstalować zestawu satelickiego w pamięci podręcznej GAC i upewnij się, że działa zgodnie z oczekiwaniami, korzystając z techniki, nazywany opóźnione podpisywanie. Jeśli opóźnienie Podpisz zestaw w czasie kompilacji można zarezerwować miejsce w pliku dla podpisu silnej nazwy. Rzeczywiste podpisywania jest opóźnione aż do później, kiedy końcowego pary kluczy publiczny/prywatny jest dostępny. Aby uzyskać więcej informacji na temat podpisywania opóźnione, zobacz [opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Uzyskiwania klucza publicznego  
 Aby opóźnić Podpisz zestaw, musi mieć dostęp do klucza publicznego. Można uzyskać klucz publiczny rzeczywistego z organizacji w firmie, czy ostatecznego podpisywania lub Utwórz klucz publiczny za pomocą [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Polecenie Sn.exe tworzy testu pary kluczy publiczny/prywatny. **— K** opcja określa, że Sn.exe należy utworzyć nowej pary kluczy i zapisać ją w pliku o nazwie TestKeyPair.snk.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Można wyodrębnić klucza publicznego z pliku, który zawiera pary kluczy testu. Polecenie wyodrębnia klucza publicznego z TestKeyPair.snk i zapisze go w PublicKey.snk:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu  
 Po Uzyskaj lub Utwórz klucz publiczny, należy użyć [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do kompilowania zestawu i określ opóźnienie podpisywania.  
  
 Polecenie Al.exe tworzy zestaw satelicki o silnych nazwach StringLibrary aplikacji z pliku strings.ja.resources:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **-Opóźnienie +** opcja określa, że konsolidator zestawów powinno opóźniać Podpisz zestaw z. **- Keyfile** opcja określa nazwę pliku klucza, który zawiera klucz publiczny opóźnienia Podpisz zestaw.  
  
### <a name="re-signing-an-assembly"></a>Ponowne podpisywanie zestawu  
 Przed wdrożeniem aplikacji należy ponownie podpisać opóźnienie podpisany zestaw satelicki z pary kluczy rzeczywistym. Można to zrobić za pomocą Sn.exe.  
  
 Polecenie Sn.exe podpisuje StringLibrary.resources.dll z pary kluczy przechowywanych w pliku RealKeyPair.snk. **– R** opcja określa, że wcześniej podpisanego lub opóźnienia podpisanych zestawów ma być ponownie podpisane.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalowanie zestawu satelickiego w globalnej pamięci podręcznej zestawów  
 Podczas wyszukiwania zasobów w proces rezerwowy zasobów środowiska uruchomieniowego, wygląda w [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md) pierwszy. (Aby uzyskać więcej informacji, zobacz sekcję "Proces rezerwowy zasobu" [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu.) Jak zestaw satelicki jest podpisany przy użyciu silnej nazwy, może być w pamięci podręcznej GAC zainstalowana za pomocą [narzędzie globalnej pamięci podręcznej zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Polecenie Gacutil.exe instaluje StringLibrary.resources.dll w globalnej pamięci podręcznej zestawów:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/I** opcja określa, że Gacutil.exe należy zainstalować określonego zestawu w globalnej pamięci podręcznej zestawów. Po satelity zestaw jest zainstalowany w nim zasobów stają się dostępne dla wszystkich aplikacji, które są przeznaczone do użycia zestawu satelickiego w pamięci podręcznej.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Zasoby w pamięci podręcznej GAC: przykład  
 W poniższym przykładzie użyto metody w bibliotece klas .NET Framework, aby wyodrębnić i zwracać zlokalizowanych pozdrowienia z pliku zasobów. Biblioteki i jej zasoby są zarejestrowane w globalnej pamięci podręcznej zestawów. Przykład obejmuje zasoby angielski (Stany Zjednoczone), francuski (Francja), rosyjski (Rosji) i kultur angielskiej wersji językowej. Język angielski jest domyślną kulturą; jego zasobów są przechowywane w zestawie głównym. Przykład opóźnienie początkowo znaki biblioteki i jej zestawy satelickie kluczem publicznym, następnie ponownie podpisuje je przy użyciu pary kluczy publiczny/prywatny. Aby utworzyć w przykładzie, wykonaj następujące czynności:  
  
1.  Jeśli nie używasz programu Visual Studio, należy użyć następującego [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenie, aby utworzyć pary kluczy publiczny/prywatny o nazwie ResKey.snk:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Jeśli używasz programu Visual Studio, użyj **podpisywanie** kartę projektu **właściwości** okno dialogowe do wygenerowania pliku klucza.  
  
2.  Należy użyć następującego [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenie, aby utworzyć plik klucza publicznego o nazwie PublicKey.snk:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Utwórz plik zasobu o nazwie Strings.resx zawiera zasobów dla kultury domyślnej. Przechowywanie jednego ciągu o nazwie `Greeting` którego wartość wynosi "Nie należy jak"? w tym pliku.  
  
4.  Do wskazywania aplikacji domyślną kulturę "en", Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybutu pliku AssemblyInfo aplikacji lub pliku kodu źródłowego głównego, który zostanie skompilowany w zestawie głównym aplikacji:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Dodaj obsługę dodatkowych kultury (kultur en US, fr-FR i ru-RU) do aplikacji w następujący sposób:  
  
    -   Do obsługi "en US" lub kultury angielski (Stany Zjednoczone), Utwórz plik zasobu o nazwie Strings.en US.resx lub Strings.en US.txt i przechowywania w nim jednego ciągu o nazwie `Greeting` którego wartość wynosi "Hello!".  
  
    -   Aby obsługiwać "fr-FR" lub kultury francuski (Francja), Utwórz plik zasobu o nazwie Strings.fr FR.resx lub Strings.fr FR.txt i przechowywania w nim jednego ciągu o nazwie `Greeting` którego wartość wynosi "BW jour!"  
  
    -   Aby obsługiwać "ru-RU" lub kultury rosyjski (Rosji), Utwórz plik zasobu o nazwie Strings.ru RU.resx lub Strings.ru RU.txt i przechowywania w nim jednego ciągu o nazwie `Greeting` którego wartość wynosi "Привет!"  
  
6.  Użyj [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) skompilować każdego tekstu lub plik zasobu XML w pliku .resources binarnego. Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jako pliki resx lub txt, ale z rozszerzeniem .resources. Jeśli utworzysz przykładzie z programem Visual Studio procesu kompilacji odbywa się automatycznie. Jeśli nie używasz programu Visual Studio, uruchom następujące polecenie, aby skompilować pliki .resx do plików .resources:  
  
    ```console
    resgen filename  
    ```  
  
     gdzie *filename* jest opcjonalna ścieżka, nazwa pliku i rozszerzenie pliku .resx lub tekst.  
  
7.  Kompiluj następujący kod źródłowy dla StringLibrary.vb lub StringLibrary.cs wraz z zasobów dla kultury domyślnej do opóźnienia podpisany zestaw biblioteki o nazwie StringLibrary.dll:  
  
    > [!IMPORTANT]
    >  Jeśli tworzenie w przykładzie przy użyciu wiersza polecenia, a nie programu Visual Studio, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> konstruktora klasy do `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     To polecenie dla kompilatora C#:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Odpowiednie polecenie kompilatora Visual Basic jest:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Utworzyć podkatalogu w katalogu głównego aplikacji dla każdego zlokalizowanych kultury obsługiwanych przez aplikację. Należy utworzyć en US, fr-FR i podkatalogu ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi jako część procesu kompilacji. Ponieważ wszystkie zestawy satelickie mają taką samą nazwę pliku, podkatalogi są używane do przechowywania zestawy satelickie specyficzne dla kultury poszczególnych, dopóki nie są podpisane przy użyciu pary kluczy publiczny/prywatny.  
  
9. Osadź poszczególnych plików .resources specyficzne dla kultury do podpisywany z opóźnieniem zestawy satelitarne i zapisać je do odpowiedniego katalogu. To polecenie, aby to zrobić dla każdego pliku .resources jest:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     gdzie *kultury* jest nazwą kultury. W tym przykładzie nazwy kultury są en US, fr-FR i ru-RU.  
  
10. Ponowne podpisanie StringLibrary.dll przy użyciu [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) w następujący sposób:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Ponowne podpisywanie zestawów satelickich indywidualnych. Aby to zrobić, użyj [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) w następujący sposób dla każdego zestawu satelickiego:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Zarejestruj StringLibrary.dll oraz wszystkich jego zestawów satelickich w globalnej pamięci podręcznej zestawów przy użyciu następującego polecenia:  
  
    ```console
    gacutil -i filename  
    ```  
  
     gdzie *filename* jest nazwa pliku do zarejestrowania.  
  
13. Jeśli używasz programu Visual Studio Utwórz nową **aplikacji konsoli** projektu o nazwie `Example`, Dodaj do niej odwołanie do StringLibrary.dll i następujący kod źródłowy i skompilować.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Aby skompilować z wiersza polecenia, wpisz następujące polecenie dla kompilatora C#:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Wiersz polecenia dla kompilatora języka Visual Basic to:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Uruchom Example.exe.  
  
## <a name="see-also"></a>Zobacz też  
 [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
