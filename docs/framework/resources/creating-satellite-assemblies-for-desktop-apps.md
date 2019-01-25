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
ms.openlocfilehash: 719f71f42ac7b0c376525ab3a316a986af0b0f43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678801"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Tworzenie zestawów satelickich dla aplikacji klasycznych
Pliki zasobów odgrywają kluczową rolę w zlokalizowanych aplikacji. Umożliwiają one aplikację, aby wyświetlić ciągi, obrazy i inne dane w przez użytkownika języka i kultury, a także do dostarczania danych alternatywnego, jeśli nie są dostępne zasoby dotyczące języka przez użytkownika lub kultury. .NET Framework wykorzystuje model Gwiazda — w celu zlokalizowania i pobrania zlokalizowanych zasobów. Piasta to główny zestaw, który zawiera niemożliwe do zlokalizowania kodu wykonywalnego i zasoby dla jednej kultury, które jest wywoływane zero lub kultury domyślnej. Domyślną kulturę używaną jest rezerwowego kulturą aplikacji; jest używany, gdy nie zlokalizowane zasoby są dostępne. Możesz użyć <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybutu, aby wyznaczyć kultury aplikacji domyślnej kultury. Każdej szprysze nawiązuje połączenie z zestawem satelickim, który zawiera zasoby dla pojedynczej zlokalizowanej kultury, ale nie zawiera żadnego kodu. Ponieważ zestawy satelickie nie są częścią zestawu głównego, można łatwo zaktualizować lub zastąpić zasoby, które odpowiadają określonej kultury bez zastępowania głównym zestawie aplikacji.  
  
> [!NOTE]
>  Zasoby aplikacji domyślnej kultury, również mogą być przechowywane w zestawie satelickim. Aby to zrobić, należy przypisać <xref:System.Resources.NeutralResourcesLanguageAttribute> wartość atrybutu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Nazwa zestawu satelickiego i lokalizacji  
 Wymaga model — Gwiazda umieść zasoby w określonych lokalizacjach, dzięki czemu mogą być łatwo znajduje się i używane. Jeśli to zrobisz nie kompilacji i nazwy zasobów, zgodnie z oczekiwaniami lub nie należy umieszczać je w odpowiednich lokalizacjach, środowisko uruchomieniowe języka wspólnego nie będzie można je znaleźć i zamiast tego użyj zasobów kultury domyślnej. Menedżer zasobów .NET Framework, reprezentowane przez <xref:System.Resources.ResourceManager> obiektów, zostanie użyta automatycznie uzyskiwać dostęp do zlokalizowanych zasobów. Resource Manager wymaga następujących elementów:  
  
-   Pojedynczy satelicki musi zawierać wszystkie zasoby dla określonej kultury. Innymi słowy należy skompilować wiele plików txt lub resx w jednym binarnego pliku Resources.  
  
-   Musi istnieć oddzielnym podkatalogu w katalogu aplikacji dla każdej zlokalizowanej kultury, przechowujący zasoby w tej kulturze. Nazwę podkatalogu musi być taka sama jak nazwa kultury. Alternatywnie można przechowywać swoje zestawy satelickie w globalnej pamięci podręcznej. W takim przypadku składnik informacji kultury silna nazwa zestawu musi wskazywać jego kultury. (Zobacz [instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów](#SN) w dalszej części tego tematu.)  
  
    > [!NOTE]
    >  Jeśli aplikacja zawiera zasoby podhodowli, umieść każdy przeszczepiania w oddzielnym podkatalogu w katalogu aplikacji. Nie należy umieszczać podhodowli podkatalogów w katalogu ich główne kultury.  
  
-   Zestawu satelickiego musi mieć taką samą nazwę jak aplikacja, a musi używać rozszerzenia nazwy pliku ". resources.dll". Na przykład jeśli aplikacja nosi nazwę Example.exe, nazwę każdego zestawu satelickiego powinna być Example.resources.dll. Należy pamiętać, że nazwa zestawu satelickiego nie wskazuje kulturę plików zasobów. Jednak zestawu satelickiego pojawia się w katalogu, który określa kulturę.  
  
-   Informacje na temat kultury zestawu satelickiego muszą być zawarte w metadanych zestawu. Aby przechować nazwę kultury w metadanych zestawu satelickiego, należy określić `/culture` opcji, gdy używasz [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) Osadzanie zasobów w zestawie satelickim.  
  
 Na poniższej ilustracji przedstawiono przykład struktury i lokalizacji wymaganiami katalogu dla aplikacji, które nie jest instalowany w [globalnej pamięci podręcznej](../../../docs/framework/app-domains/gac.md). Elementy z rozszerzeniami txt i Resources nie będą dostarczane wraz z ostatnim aplikacji. Są to pliki zasobów pośredniego, używany do tworzenia zestawów zasobów satelickich końcowego. W tym przykładzie można zastąpić pliki resx na pliki txt. Aby uzyskać więcej informacji, zobacz [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Zestawy satelickie](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Katalog zestawu satelickiego  
  
## <a name="compiling-satellite-assemblies"></a>Kompilowanie zestawów satelickich  
 Możesz użyć [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do kompilowania plików tekstowych lub pliki XML (resx), które zawierają zasoby do binarnych plików Resources. Następnie użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do kompilowania plików Resources do zestawów satelickich. Al.exe tworzy zestaw z plików Resources, które określisz. Zestawy satelickie może zawierać tylko zasoby; nie mogą zawierać dowolny kod wykonywalny.  
  
 Następujące polecenie Al.exe tworzy zestaw satelicki dla aplikacji `Example` z strings.de.resources pliku zasobów w Niemczech.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Następujące polecenie Al.exe tworzy również zestaw satelicki dla aplikacji `Example` z strings.de.resources pliku. **Template** opcja powoduje, że zestawu satelickiego można odziedziczyć wszystkie metadane zestawu, z wyjątkiem jego informacje o ustawieniach kulturowych z nadrzędnego zestawu (Example.dll).  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 W poniższej tabeli opisano opcje Al.exe używane w tych poleceniach bardziej szczegółowo.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-target:** lib|Określa, że Twojego zestawu satelickiego jest kompilowany do pliku biblioteki (.dll). Ponieważ nie zawiera kodu wykonywalnego typowe dla zestawu satelickiego, a nie jest głównym zestawem aplikacji, należy zapisać zestawów satelickich bibliotek DLL.|  
|**-embed:** strings.de.resources|Określa nazwę pliku zasobów do osadzania, gdy Al.exe kompiluje zestaw. Możesz osadzić wiele plików Resources w zestawie satelickim, ale jeśli korzystasz z modelu Gwiazda, należy skompilować jeden zestaw satelicki dla poszczególnych kultur. Można jednak utworzyć oddzielnych plików Resources ciągi i obiekty.|  
|**-kultury:** de|Określa kulturę zasobów do kompilacji. Środowisko uruchomieniowe języka wspólnego używa tych informacji podczas wyszukiwania zasobów dla określonej kultury. Jeżeli pominięto tę opcję, Al.exe będzie nadal kompilować zasobu, ale środowisko wykonawcze nie będzie można znaleźć go, gdy użytkownik zażąda.|  
|**-out:** Example.resources.dll|Określa nazwę pliku wyjściowego. Nazwa musi być zgodna standard nazewnictwa *baseName*.resources. *rozszerzenie*, gdzie *baseName* jest nazwą zestawu głównego i *rozszerzenia* jest prawidłowe rozszerzenie (na przykład .dll). Należy pamiętać, że środowisko uruchomieniowe nie jest możliwe ustalenie kultury zestawu satelickiego na podstawie jego nazwy pliku wyjściowego; należy użyć **/kulturze** opcję, aby je określić.|  
|**-szablon:** Example.dll|Określa zestaw, z którego zestawu satelickiego będzie dziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultury. Ta opcja dotyczy zestawów satelickich, tylko wtedy, gdy należy określić zestaw, który ma [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Aby uzyskać pełną listę i opcje Al.exe, zobacz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Zestawy satelitarne: Przykład  
 Poniżej przedstawiono prosty przykład "Hello world", która wyświetla okno komunikatu, zawierającą zlokalizowane powitanie. Przykład zawiera zasoby dla języka angielskiego (Stany Zjednoczone), francuski (Francja) i kultur rosyjski (Rosja), a jego rezerwowego kultury jest język angielski. Aby utworzyć przykładu, wykonaj następujące czynności:  
  
1.  Utwórz plik zasobów o nazwie Greeting.resx lub Greeting.txt, aby zawierała zasobów dla kultury domyślnej. Pojedynczy ciąg o nazwie Store `HelloString` którego wartością jest "Hello world!" w tym pliku.  
  
2.  Do wskazywania aplikacji domyślnej kultury angielski (en), Dodaj następujący kod <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybutu do pliku AssemblyInfo aplikacji lub do pliku kodu źródłowego głównego, który zostanie skompilowany w głównym zestawie aplikacji.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Dodanie obsługi dodatkowych kultur (en US, fr-FR i ru-RU) do aplikacji w następujący sposób:  
  
    -   Do obsługi en US lub kultury angielski (Stany Zjednoczone), Utwórz plik zasobów o nazwie Greeting.en US.resx lub Greeting.en US.txt, a w niej przechowywane jako jeden ciąg znaków o nazwie `HelloString` którego wartością jest "Witaj świecie!"  
  
    -   Na potrzeby obsługi, fr-FR lub kultury francuski (Francja), Utwórz plik zasobów o nazwie Greeting.fr-FR.resx lub Greeting.fr FR.txt, a w niej przechowywane jako jeden ciąg znaków o nazwie `HelloString` którego wartością jest "Salut w całości le monde!"  
  
    -   Na potrzeby obsługi, ru-RU lub kultury rosyjski (Rosja), Utwórz plik zasobów o nazwie Greeting.ru RU.resx lub Greeting.ru RU.txt, a w niej przechowywane jako jeden ciąg znaków o nazwie `HelloString` którego wartością jest "Всем привет!"  
  
4.  Użyj [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) skompilować każdego tekstowym lub XML pliku zasobu do binarnego pliku Resources. Dane wyjściowe to zbiór plików, które mają taką samą nazwę pliku głównego, jak pliki resx lub .txt, ale z rozszerzeniem Resources. Po utworzeniu przykładu z programu Visual Studio, proces kompilacji odbywa się automatycznie. Jeśli nie używasz programu Visual Studio, uruchom następujące polecenia do kompilowania plików resx na pliki Resources:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     Jeśli zasoby w plikach tekstowych zamiast plików XML, Zamień .txt rozszerzeniem resx.  
  
5.  Skompiluj następujący kod źródłowy, wraz z zasobów dla kultury domyślnej do zestawu głównej aplikacji:  
  
    > [!IMPORTANT]
    >  Korzystając z wiersza polecenia, a nie programu Visual Studio do tworzenia przykładu, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> konstruktora klasy do następującego: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Jeśli aplikacja nosi nazwę przykładu i kompilujesz z wiersza polecenia, polecenie dla C# kompilator jest:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Odpowiednie polecenie kompilator języka Visual Basic to:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Tworzenie podkatalogu w katalogu głównym aplikacji, dla każdej zlokalizowanej kultury, obsługiwanych przez aplikację. Należy utworzyć en US, fr-FR i podkatalogu ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi jako część procesu kompilacji.  
  
7.  Osadzanie plików poszczególnych Resources specyficzne dla kultury w zestawy satelickie i zapisują je do odpowiedniego katalogu. To polecenie, aby to zrobić dla każdego pliku Resources:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     gdzie *kultury* jest nazwą kultury, którego zasoby, które zawiera zestawu satelickiego. Visual Studio, które automatycznie obsługuje ten proces.  
  
 Następnie można uruchomić przykład. Losowo wprowadzi jednym z obsługiwanych kulturami bieżącej kultury i wyświetlić pozdrowienia zlokalizowane.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalowanie zestawów satelickich w globalnej pamięci podręcznej  
 Zamiast instalować zestawów w podkatalogu lokalnej aplikacji, można zainstalować je w globalnej pamięci podręcznej. Jest to szczególnie przydatne, jeśli masz bibliotek klas i zestawów zasobów biblioteki klasy, które są używane przez wiele aplikacji.  
  
 Instalowanie zestawów w globalnej pamięci podręcznej wymaga, że mają one silne nazwy. Zestawy o silnych nazwach są podpisane za pomocą prawidłowej pary kluczy publiczny/prywatny. Zawierają one informacje o wersji, która używa środowiska uruchomieniowego, aby określić które zestawu na potrzeby spełnienia żądania powiązania. Aby uzyskać więcej informacji na temat silne nazwy i wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md). Aby uzyskać więcej informacji o silnych nazwach, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Opracowując aplikację, jest mało prawdopodobne, że masz dostęp do końcowego pary kluczy publiczny/prywatny. Aby można było zainstalować zestawu satelickiego w globalnej pamięci podręcznej i upewnij się, że działa zgodnie z oczekiwaniami, można użyć technikę o nazwie opóźnionego podpisywania. Gdy opóźnienie Podpisz zestaw w czasie kompilacji możesz zarezerwować miejsce w pliku podpisu silnej nazwy. Rzeczywiste podpisywania jest opóźnione dopiero po pewnym czasie, gdy ostateczny pary kluczy publiczny/prywatny jest dostępna. Aby uzyskać więcej informacji na temat opóźnionego podpisywania, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Uzyskiwanie klucza publicznego  
 Aby opóźnić Podpisz zestaw, musi mieć dostęp do klucza publicznego. Można uzyskać klucz publiczny rzeczywiste z organizacji w Twojej firmie, czy ostatecznej podpisywanie, lub Utwórz klucz publiczny za pomocą [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Następujące polecenie Sn.exe tworzy parę kluczy publiczny/prywatny testu. **– K** opcja określa, że Sn.exe, należy utworzyć nową parę kluczy i zapisz go w pliku o nazwie TestKeyPair.snk.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Można wyodrębnić klucza publicznego z pliku, który zawiera parę kluczy testu. Poniższe polecenie wyodrębnia klucz publiczny z TestKeyPair.snk i zapisuje je w PublicKey.snk:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu  
 Po Uzyskaj lub Utwórz klucz publiczny, należy użyć [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do kompilowania zestawu i określ opóźnionego podpisywania.  
  
 Poniższe polecenie Al.exe tworzy zestaw o silnej nazwie satelicki dla aplikacji StringLibrary z pliku strings.ja.resources:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **-Delay +** opcja określa, że konsolidator zestawów, należy opóźnić podpisanie zestawu. **- Keyfile** opcja określa nazwę pliku klucza, który zawiera klucz publiczny, który umożliwia opóźnienie podpisywania zestawu.  
  
### <a name="re-signing-an-assembly"></a>Ponowne podpisywanie zestawu  
 Przed wdrożeniem aplikacji musisz ją ponownie podpisać opóźnienie podpisanego zestawu satelickiego parą kluczy liczby rzeczywistej. Można to zrobić przy użyciu Sn.exe.  
  
 Poniższe polecenie Sn.exe podpisuje StringLibrary.resources.dll parą kluczy przechowywanych w pliku RealKeyPair.snk. **– R** opcja określa, że wcześniej podpisane lub opóźnienia, podpisać zestaw jest ponownie podpisana.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalowanie zestawu satelickiego w globalnej pamięci podręcznej  
 Gdy środowisko uruchomieniowe wyszukuje zasobów w proces bazowy zasobu, szuka w [globalnej pamięci podręcznej](../../../docs/framework/app-domains/gac.md) pierwszy. (Aby uzyskać więcej informacji, zobacz sekcję "Zasobów rezerwowych procesu" [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu.) Jak najszybciej zestawu satelickiego jest podpisany silną nazwą, jego można zainstalować w globalnej pamięci podręcznej przy użyciu [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Poniższe polecenie Gacutil.exe instaluje StringLibrary.resources.dll w globalnej pamięci podręcznej:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/I** opcja określa, że Gacutil.exe należy zainstalować określony zestaw w globalnej pamięci podręcznej. Po satelity zestaw jest zainstalowany w pamięci podręcznej, zasoby, które zawiera stają się dostępne dla wszystkich aplikacji, które są przeznaczone do użycia zestawu satelickiego.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Zasoby w globalnej pamięci podręcznej: Przykład  
 W poniższym przykładzie użyto metody w bibliotece klas .NET Framework, aby wyodrębnić i zwraca zlokalizowany pozdrowienia z pliku zasobów. Biblioteki i jej zasoby są zarejestrowane w globalnej pamięci podręcznej. Przykład zawiera zasoby dla języka angielskiego (Stany Zjednoczone), francuski (Francja), rosyjski (Rosja) i angielskim kultur. Język angielski jest domyślną kulturą; jego zasobów są przechowywane w głównym zestawie. Przykład opóźnienie początkowo objawy biblioteki i jej zestawy satelickie z kluczem publicznym, następnie podpisuje ponownie je parą kluczy publiczny/prywatny. Aby utworzyć przykładu, wykonaj następujące czynności:  
  
1.  Jeśli nie używasz programu Visual Studio, należy użyć następującego [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenie, aby utworzyć parę kluczy publiczny/prywatny, o nazwie ResKey.snk:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Jeśli używasz programu Visual Studio, użyj **podpisywanie** projektu na karcie **właściwości** okno dialogowe, aby wygenerować plik klucza.  
  
2.  Należy użyć następującego [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenie, aby utworzyć plik klucza publicznego o nazwie PublicKey.snk:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Utwórz plik zasobów o nazwie Strings.resx zawierać zasobów dla kultury domyślnej. Pojedynczy ciąg o nazwie Store `Greeting` którego wartością jest "Jak czy ich czy?" w tym pliku.  
  
4.  Do wskazywania aplikacji domyślnej kultury "en", Dodaj następujący kod <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybutu do pliku AssemblyInfo aplikacji lub do pliku kodu źródłowego głównego, który zostanie skompilowany w głównym zestawie aplikacji:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Dodanie obsługi dodatkowych kultur (kultury en US, fr-FR i ru-RU) do aplikacji w następujący sposób:  
  
    -   Aby obsługiwać "en US" lub kultury angielski (Stany Zjednoczone), Utwórz plik zasobów o nazwie Strings.en US.resx lub Strings.en US.txt, a w niej przechowywane jako jeden ciąg znaków o nazwie `Greeting` którego wartością jest "Hello!".  
  
    -   Aby obsługiwać "fr-FR" lub kultury francuski (Francja), Utwórz plik zasobów o nazwie Strings.fr-FR.resx lub Strings.fr FR.txt i przechowywanych w niej pojedynczego ciągu o nazwie `Greeting` którego wartością jest "Bon jour!"  
  
    -   Aby obsługiwać "ru-RU" lub kultury rosyjski (Rosja), Utwórz plik zasobów o nazwie Strings.ru RU.resx lub Strings.ru RU.txt i przechowywanych w niej pojedynczego ciągu o nazwie `Greeting` którego wartością jest "Привет!"  
  
6.  Użyj [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) skompilować każdego tekstowym lub XML pliku zasobu do binarnego pliku Resources. Dane wyjściowe to zbiór plików, które mają taką samą nazwę pliku głównego, jak pliki resx lub .txt, ale z rozszerzeniem Resources. Po utworzeniu przykładu z programu Visual Studio, proces kompilacji odbywa się automatycznie. Jeśli nie używasz programu Visual Studio, uruchom następujące polecenie do kompilowania plików resx na pliki Resources:  
  
    ```console
    resgen filename  
    ```  
  
     gdzie *filename* jest opcjonalna ścieżka, nazwa pliku i rozszerzenie pliku tekstowych lub resx.  
  
7.  Kompiluj następujący kod źródłowy dla StringLibrary.vb lub StringLibrary.cs wraz z zasobów dla kultury domyślnej do opóźnienia podpisanego zestawu biblioteki o nazwie StringLibrary.dll:  
  
    > [!IMPORTANT]
    >  Korzystając z wiersza polecenia, a nie programu Visual Studio do tworzenia przykładu, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> Konstruktor `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     Polecenie dla C# kompilator jest:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Odpowiednie polecenie kompilator języka Visual Basic to:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Tworzenie podkatalogu w katalogu głównym aplikacji, dla każdej zlokalizowanej kultury, obsługiwanych przez aplikację. Należy utworzyć en US, fr-FR i podkatalogu ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi jako część procesu kompilacji. Ponieważ wszystkie zestawy satelickie mają taką samą nazwę, podkatalogi są używane do przechowywania poszczególnych specyficzne dla kultury zestawy satelickie, dopóki nie są podpisane parą kluczy publiczny/prywatny.  
  
9. Osadzanie poszczególnych plików Resources specyficzne dla kultury do podpisany z opóźnieniem zestawy satelickie i zapisują je do odpowiedniego katalogu. To polecenie, aby to zrobić dla każdego pliku Resources:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     gdzie *kultury* jest nazwa kultury. W tym przykładzie nazwy kultury są en US, fr-FR i ru-RU.  
  
10. Ponowne podpisywanie StringLibrary.dll przy użyciu [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) w następujący sposób:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Ponowne podpisywanie zestawów satelickich indywidualnych. Aby to zrobić, należy użyć [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) w następujący sposób dla każdego zestawu satelickiego:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Zarejestruj StringLibrary.dll, a każdy z jego zestawów satelickich w globalnej pamięci podręcznej przy użyciu następującego polecenia:  
  
    ```console
    gacutil -i filename  
    ```  
  
     gdzie *filename* to nazwa pliku do zarejestrowania.  
  
13. Jeśli używasz programu Visual Studio Utwórz nowy **aplikacji konsoli** projektu o nazwie `Example`, Dodaj do niej odwołanie do StringLibrary.dll i następujący kod źródłowy i kompilacji.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Aby skompilować z wiersza polecenia, użyj następującego polecenia do C# kompilatora:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Wiersz polecenia dla kompilatora języka Visual Basic jest:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Uruchom Example.exe.  
  
## <a name="see-also"></a>Zobacz także
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
