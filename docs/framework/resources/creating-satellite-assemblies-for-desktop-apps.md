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
ms.openlocfilehash: 29739625d29db6dc7c3876007f1e733b15f5c026
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970991"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Tworzenie zestawów satelickich dla aplikacji klasycznych

Pliki zasobów odgrywają centralną rolę w zlokalizowanych aplikacjach. Umożliwiają one aplikacji wyświetlanie ciągów, obrazów i innych danych w własnym języku i kulturze użytkownika oraz dostarczanie alternatywnych danych, jeśli zasoby dla własnego języka lub kultury użytkownika są niedostępne. .NET Framework używa modelu gwiazdy, aby zlokalizować i pobrać zlokalizowane zasoby. Koncentrator jest głównym zestawem zawierającym nielokalizowalny kod wykonywalny i zasoby dla jednej kultury, która jest nazywana kulturą neutralną lub domyślną. Domyślna kultura jest kulturą rezerwową dla aplikacji; jest on używany, gdy nie są dostępne żadne zlokalizowane zasoby. Użyj atrybutu, <xref:System.Resources.NeutralResourcesLanguageAttribute> aby wyznaczyć kulturę domyślnej kultury aplikacji. Każdy szprych nawiązuje połączenie z zestawem satelickim zawierającym zasoby dla jednej zlokalizowanej kultury, ale nie zawiera kodu. Ponieważ zestawy satelickie nie są częścią głównego zestawu, można łatwo aktualizować lub zastępować zasoby, które odpowiadają określonej kulturze, bez zastępowania głównego zestawu aplikacji.

> [!NOTE]
> Zasoby domyślnej kultury aplikacji mogą być również przechowywane w zestawie satelickim. W tym celu należy przypisać <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut o <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>wartości.

## <a name="satellite-assembly-name-and-location"></a>Nazwa i lokalizacja zestawu satelickiego

Model gwiazdy i gwiazdy wymaga umieszczenia zasobów w określonych lokalizacjach, aby można je było łatwo zlokalizować i wykorzystać. Jeśli nie kompilujesz zasobów i nie nazywasz ich w oczekiwany sposób lub jeśli nie umieścisz ich w prawidłowych lokalizacjach, środowisko uruchomieniowe języka wspólnego nie będzie w stanie go zlokalizować i będzie używać zasobów kultury domyślnej. .NET Framework Menedżer zasobów reprezentowane przez <xref:System.Resources.ResourceManager> obiekt jest używany do automatycznego uzyskiwania dostępu do zlokalizowanych zasobów. Menedżer zasobów wymaga następujących czynności:

- Pojedynczy zestaw satelicki musi zawierać wszystkie zasoby dla określonej kultury. Innymi słowy, należy skompilować wiele plików txt lub resx do jednego pliku binarnego Resources.

- W katalogu aplikacji musi znajdować się oddzielny podkatalog dla każdej zlokalizowanej kultury, która przechowuje zasoby danej kultury. Nazwa podkatalogu musi być taka sama jak nazwa kultury. Alternatywnie można przechowywać zestawy satelickie w globalnej pamięci podręcznej zestawów. W takim przypadku składnik informacji o kulturze silnej nazwy zestawu musi wskazywać jego kulturę. (Zobacz [Instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów w](#SN) dalszej części tego tematu).

  > [!NOTE]
  > Jeśli aplikacja zawiera zasoby dla podkultur, umieść każdą podkulturę w osobnym podkatalogu w katalogu aplikacji. Nie należy umieszczać podkultur w podkatalogach w katalogu kultury głównej.

- Zestaw satelicki musi mieć taką samą nazwę jak aplikacja i musi używać rozszerzenia nazwy pliku ". resources. dll". Na przykład jeśli aplikacja ma nazwę example. exe, Nazwa każdego zestawu satelickiego powinna być przykładem. resources. dll. Należy zauważyć, że nazwa zestawu satelickiego nie wskazuje kultury plików zasobów. Jednak zestaw satelicki pojawia się w katalogu, który określa kulturę.

- Informacje o kulturze zestawu satelickiego muszą być zawarte w metadanych zestawu. Aby zapisać nazwę kultury w metadanych zestawu satelickiego, należy określić `/culture` opcję przy użyciu [konsolidatora zestawu](../tools/al-exe-assembly-linker.md) do osadzenia zasobów w zestawie satelickim.

Na poniższej ilustracji przedstawiono przykładową strukturę katalogów i wymagania dotyczące lokalizacji dla aplikacji, które nie są instalowane w [globalnej pamięci podręcznej zestawów](../../framework/app-domains/gac.md). Elementy z rozszerzeniami. txt i. resources nie będą dostarczane z aplikacją końcową. Są to pośrednie pliki zasobów używane do tworzenia końcowych zestawów zasobów satelitarnych. W tym przykładzie można zastąpić pliki RESX dla plików txt. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md).

Na poniższej ilustracji przedstawiono katalog zestawu satelickiego:

![Katalog zestawu satelickiego ze zlokalizowanymi podkatalogami kultury.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a>Kompilowanie zestawów satelickich

Używasz [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) do kompilowania plików tekstowych lub plików XML (. resx) zawierających zasoby do plików binarnych. resources. Następnie należy użyć [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) do kompilowania plików Resources do zestawów satelickich. Al. exe tworzy zestaw z plików Resources, które określisz. Zestawy satelickie mogą zawierać tylko zasoby; nie mogą zawierać żadnego kodu wykonywalnego.

Następujące polecenie Al. exe tworzy zestaw satelicki dla aplikacji `Example` z ciągów plików zasobów niemieckich. de. resources.

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

Następujące polecenie Al. exe tworzy również zestaw satelicki dla aplikacji `Example` z ciągów plików. de. resources. Opcja **/Template** powoduje, że zestaw satelicki dziedziczy wszystkie metadane zestawu, z wyjątkiem informacji o kulturze z zestawu nadrzędnego (przykład. dll).

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
 W poniższej tabeli opisano opcje Al. exe używane w tych poleceniach bardziej szczegółowo.
  
|Opcja|Opis|
|------------|-----------------|
|**-target:** lib|Określa, że zestaw satelicki jest kompilowany do pliku biblioteki (. dll). Ponieważ zestaw satelicki nie zawiera kodu wykonywalnego i nie jest głównym zestawem aplikacji, należy zapisać zestawy satelickie jako biblioteki DLL.|
|**-embed:** String. de. resources|Określa nazwę pliku zasobu do osadzenia, gdy Al. exe kompiluje zestaw. Można osadzić wiele plików Resources w zestawie satelickim, ale jeśli korzystasz z modelu gwiazdy i szprych, musisz skompilować jeden zestaw satelicki dla każdej kultury. Można jednak tworzyć oddzielne pliki resources dla ciągów i obiektów.|
|**-kultura:** de|Określa kulturę zasobu do skompilowania. Środowisko uruchomieniowe języka wspólnego używa tych informacji podczas wyszukiwania zasobów dla określonej kultury. W przypadku pominięcia tej opcji Al. exe będzie nadal kompilować zasób, ale środowisko uruchomieniowe nie będzie mogło go znaleźć, gdy użytkownik zażąda.|
|**-out:** Przykład. resources. dll|Określa nazwę pliku wyjściowego. Nazwa musi następować po nazewnictwie standard *basename*. resources. *rozszerzenie*, gdzie *basename* jest nazwą głównego zestawu, a *rozszerzenie* jest prawidłowym rozszerzeniem nazwy pliku (np. dll). Należy pamiętać, że środowisko uruchomieniowe nie może określić kultury zestawu satelickiego na podstawie jego nazwy pliku wyjściowego; Aby to określić, należy użyć opcji **/Culture** .|
|**-szablon:** Przykład. dll|Określa zestaw, z którego zestaw satelicki będzie dziedziczyć wszystkie metadane zestawu z wyjątkiem pola kultury. Ta opcja ma wpływ na zestawy satelickie tylko w przypadku określenia zestawu o [silnej nazwie](../../standard/assembly/strong-named.md).|
  
 Aby zapoznać się z pełną listą opcji dostępnych w programie Al. exe, zobacz [konsolidator zestawu (Al. exe)](../tools/al-exe-assembly-linker.md).
  
## <a name="satellite-assemblies-an-example"></a>Zestawy satelickie: Przykład  
 Poniżej znajduje się prosty przykład "Hello World", który wyświetla okno komunikatu zawierające zlokalizowane powitanie. W przykładzie uwzględniono zasoby dla kultur angielskiej (Stany Zjednoczone), francuski (Francja) i rosyjski (Rosja), a jej kultura rezerwowa jest w języku angielskim. Aby utworzyć przykład, wykonaj następujące czynności:  
  
1. Utwórz plik zasobów o nazwie Greetings. resx lub Greeting. txt, aby zawierał zasób dla kultury domyślnej. Przechowywanie pojedynczego ciągu o nazwie `HelloString` "Hello World!" w tym pliku.
  
2. Aby wskazać, że angielski (EN) jest kulturą domyślną aplikacji, Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybut do pliku AssemblyInfo aplikacji lub do głównego pliku kodu źródłowego, który zostanie skompilowany do głównego zestawu aplikacji.
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. Dodaj obsługę dodatkowych kultur (EN-US, fr-FR i ru-RU) do aplikacji w następujący sposób:  
  
    - Aby zapewnić obsługę kultury en-us lub English (Stany Zjednoczone), Utwórz plik zasobów o nazwie Greetings. en-us. resx lub Greetings. en-us. txt i Zapisz w nim w tym samym ciągu o `HelloString` nazwie "Witaj świecie!"  
  
    - Aby zapewnić obsługę kultury fr-fr lub francuski (Francja), Utwórz plik zasobów o nazwie Greeting.fr-fr. resx lub Greeting.fr-fr. txt, a następnie zapisz go w tym samym ciągu `HelloString` o nazwie, którego wartość to "Salut Tout Le Monde!"  
  
    - Aby zapewnić obsługę kultury ru-RU lub rosyjski (Rosja), Utwórz plik zasobów o nazwie Greeting.ru-RU. resx lub Greeting.ru-RU. txt i Zapisz w nim pojedynczy ciąg o nazwie `HelloString` "Всем Привет!"  
  
4. Użyj programu [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) , aby skompilować każdy plik tekstowy lub XML do pliku binarnego. resources. Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jak pliki resx lub txt, ale rozszerzenie. resources. Jeśli utworzysz przykład w programie Visual Studio, proces kompilacji jest obsługiwany automatycznie. Jeśli nie korzystasz z programu Visual Studio, uruchom następujące polecenia, aby skompilować pliki. resx do plików Resources:  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    Jeśli zasoby znajdują się w plikach tekstowych zamiast plików XML, Zastąp rozszerzenie resx rozszerzeniem. txt.

5. Skompiluj następujący kod źródłowy wraz z zasobami dla domyślnej kultury w zestawie głównym aplikacji:

    > [!IMPORTANT]
    > Jeśli używasz wiersza polecenia zamiast programu Visual Studio do utworzenia przykładu, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> konstruktora klasy w następujący sposób:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    Jeśli aplikacja jest przykładowa i jest kompilowana z wiersza polecenia, polecenie dla C# kompilatora jest następujące:

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    Odpowiednie polecenie kompilatora Visual Basic:

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. Utwórz podkatalog w katalogu głównym aplikacji dla każdej zlokalizowanej kultury obsługiwanej przez aplikację. Należy utworzyć podkatalog en-US, fr-FR i ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi w ramach procesu kompilacji.

7. Osadź poszczególne pliki zasobów specyficzne dla kultury w zestawach satelickich i Zapisz je w odpowiednim katalogu. Polecenie to zrób dla każdego pliku Resources:

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```  
  
     gdzie *Culture* to nazwa kultury, której zasoby zawierają zestaw satelicki. Program Visual Studio obsługuje ten proces automatycznie.
  
 Następnie można uruchomić przykład. Spowoduje to losowo przetworzenie jednej z obsługiwanych kultur w bieżącej kulturze i wyświetlenie zlokalizowanego powitania.
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów  
 Zamiast instalować zestawy w lokalnym podkatalogu aplikacji, można je zainstalować w globalnej pamięci podręcznej zestawów. Jest to szczególnie przydatne, jeśli dysponujesz bibliotekami klas i zestawami zasobów biblioteki klas, które są używane przez wiele aplikacji.
  
 Instalowanie zestawów w globalnej pamięci podręcznej zestawów wymaga posiadania silnych nazw. Zestawy o silnych nazwach są podpisane przy użyciu prawidłowej pary kluczy publiczny/prywatny. Zawierają informacje o wersji używane przez środowisko uruchomieniowe do określenia zestawu, który ma być używany w celu spełnienia żądania powiązania. Aby uzyskać więcej informacji na temat silnych nazw i wersji, zobacz [wersja zestawu](../../standard/assembly/versioning.md). Aby uzyskać więcej informacji o silnych nazwach, zobacz [zestawy o silnych nazwach](../../standard/assembly/strong-named.md).
  
 Podczas tworzenia aplikacji jest mało prawdopodobne, że będziesz mieć dostęp do ostatniej pary kluczy publiczny/prywatny. W celu zainstalowania zestawu satelickiego w globalnej pamięci podręcznej zestawów i upewnienia się, że działa zgodnie z oczekiwaniami, można użyć techniki o nazwie opóźnione podpisywanie. Gdy opóźniasz podpisywanie zestawu w czasie kompilacji, Zarezerwuj miejsce w pliku dla sygnatury silnej nazwy. Rzeczywiste podpisywanie jest opóźnione aż do późniejszego momentu udostępnienia ostatniej pary kluczy publiczny/prywatny. Aby uzyskać więcej informacji na temat opóźnionego podpisywania, zobacz [opóźnienie podpisywania zestawu](../../standard/assembly/delay-sign.md).
  
### <a name="obtaining-the-public-key"></a>Uzyskiwanie klucza publicznego  
 Aby opóźnić podpisywanie zestawu, musisz mieć dostęp do klucza publicznego. Możesz uzyskać rzeczywisty klucz publiczny z organizacji w firmie, który będzie podpisywać ostateczne lub utworzyć klucz publiczny za pomocą [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md).
  
 Następujące polecenie SN. exe tworzy parę kluczy publiczny/prywatny. Opcja **– k** określa, że SN. exe powinien utworzyć nową parę kluczy i zapisać ją w pliku o nazwie TestKeyPair. snk.
  
```console
sn –k TestKeyPair.snk
```

Klucz publiczny można wyodrębnić z pliku, który zawiera parę kluczy testowych. Następujące polecenie wyodrębnia klucz publiczny z TestKeyPair. snk i zapisuje go w PublicKey. snk:

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu

Po uzyskaniu lub utworzeniu klucza publicznego należy użyć [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) do skompilowania zestawu i określić opóźnione podpisywanie.

Następujące polecenie Al. exe tworzy zestaw o silnej nazwie satelicki dla aplikacji StringLibrary z pliku String. ja. Resources:

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

Opcja **-delay +** określa, że konsolidator zestawu powinien opóźnić podpisywanie zestawu. Opcja **-KeyFile** określa nazwę pliku klucza, który zawiera klucz publiczny używany do opóźniania podpisywania zestawu.

### <a name="re-signing-an-assembly"></a>Ponowne podpisywanie zestawu

Przed wdrożeniem aplikacji należy ponownie podpisać Wbudowany zestaw satelicki z opóźnieniem przy użyciu pary kluczy rzeczywistych. Można to zrobić za pomocą SN. exe.

Następujące polecenie SN. exe znakuje StringLibrary. resources. dll z parą kluczy przechowywaną w pliku RealKeyPair. snk. Opcja **– R** określa, że wcześniej podpisany lub opóźniony zestaw podpisany z opóźnieniem ma być podpisywany.

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Instalowanie zestawu satelickiego w globalnej pamięci podręcznej zestawów

Gdy środowisko uruchomieniowe wyszukuje zasoby w procesie rezerwowym zasobów, najpierw przeszukuje [globalną pamięć podręczną zestawów](../../framework/app-domains/gac.md) . (Aby uzyskać więcej informacji, zobacz sekcję "proces rezerwowy zasobów" tematu [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md) ). Gdy tylko zestaw satelicki zostanie podpisany przy użyciu silnej nazwy, można go zainstalować w globalnej pamięci podręcznej zestawów przy użyciu [Global Assembly Cache Tool (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md).

Następujące polecenie Gacutil. exe instaluje StringLibrary. resources. dll w globalnej pamięci podręcznej zestawów:

```console
gacutil -i:StringLibrary.resources.dll
```

**/I** opcja określa, że Gacutil. exe powinien zainstalować określony zestaw w globalnej pamięci podręcznej zestawów. Po zainstalowaniu zestawu satelickiego w pamięci podręcznej zasoby, które zawiera, staną się dostępne dla wszystkich aplikacji, które są przeznaczone do korzystania z zestawu satelickiego.

### <a name="resources-in-the-global-assembly-cache-an-example"></a>Zasoby w globalnej pamięci podręcznej zestawów: Przykład

Poniższy przykład używa metody w bibliotece klas .NET Framework, aby wyodrębnić i zwrócić zlokalizowane powitanie z pliku zasobów. Biblioteka i jej zasoby są zarejestrowane w globalnej pamięci podręcznej zestawów. Przykład zawiera zasoby dla angielskiej wersji językowej (Stany Zjednoczone), francuski (Francja), rosyjski (Rosja) i kulturę w języku angielskim. Język angielski jest kulturą domyślną; jego zasoby są przechowywane w zestawie głównym. Przykładowe opóźnienie polega na podpisaniu biblioteki i jej zestawów satelickich za pomocą klucza publicznego, a następnie ponowne podpisanie ich za pomocą pary kluczy publicznych/prywatnych. Aby utworzyć przykład, wykonaj następujące czynności:

1. Jeśli nie używasz programu Visual Studio, użyj następującego polecenia [silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) , aby utworzyć parę kluczy publiczny/prywatny o nazwie ResKey. snk:

    ```console
    sn –k ResKey.snk
    ```

    Jeśli używasz programu Visual Studio, Użyj karty **podpisywanie** okna dialogowego **Właściwości** projektu, aby wygenerować plik klucza.

2. Użyj poniższego polecenia [silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) , aby utworzyć plik klucza publicznego o nazwie PublicKey. snk:

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. Utwórz plik zasobów o nazwie Strings. resx, aby zawierał zasób domyślnej kultury. Przechowaj pojedynczy ciąg o `Greeting` nazwie, którego wartość to "jak to zrobić"? w tym pliku.

4. Aby wskazać, że "en" jest kulturą domyślną aplikacji, Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybut do pliku AssemblyInfo aplikacji lub do głównego pliku kodu źródłowego, który zostanie skompilowany do głównego zestawu aplikacji:

    [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. Dodanie obsługi dodatkowych kultur (kultur en-US, fr-FR i ru-RU) do aplikacji w następujący sposób:

    - Aby zapewnić obsługę kultury "en-us" lub angielski (Stany Zjednoczone), Utwórz plik zasobów o nazwie Strings. en-us. resx lub String. en-us. txt i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "Hello!".

    - Aby zapewnić obsługę kultury "fr-fr" lub francuski (Francja), Utwórz plik zasobów o nazwie Strings.fr-fr. resx lub Strings.fr-fr. txt i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "szczęśliwe jour!"

    - Aby zapewnić obsługę kultury "ru-RU" lub rosyjski (Rosja), Utwórz plik zasobów o nazwie Strings.ru-RU. resx lub Strings.ru-RU. txt i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "Привет!"

6. Użyj programu [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) , aby skompilować każdy plik tekstowy lub XML do pliku binarnego. resources. Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jak pliki resx lub txt, ale rozszerzenie. resources. Jeśli utworzysz przykład w programie Visual Studio, proces kompilacji jest obsługiwany automatycznie. Jeśli nie korzystasz z programu Visual Studio, uruchom następujące polecenie, aby skompilować pliki. resx do plików Resources:

    ```console
    resgen filename
    ```

    gdzie *filename* to opcjonalna ścieżka, nazwa pliku i rozszerzenie pliku resx lub tekstu.

7. Skompiluj następujący kod źródłowy dla StringLibrary. vb lub StringLibrary.cs wraz z zasobami dla kultury domyślnej w zestawie bibliotek podpisanych z opóźnieniem o nazwie StringLibrary. dll:

    > [!IMPORTANT]
    > Jeśli używasz wiersza polecenia zamiast programu Visual Studio do utworzenia przykładu, należy zmodyfikować wywołanie <xref:System.Resources.ResourceManager> konstruktora klasy do. `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    Polecenie dla C# kompilatora jest następujące:

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    Odpowiednie polecenie kompilatora Visual Basic:

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. Utwórz podkatalog w katalogu głównym aplikacji dla każdej zlokalizowanej kultury obsługiwanej przez aplikację. Należy utworzyć podkatalog en-US, fr-FR i ru-RU. Program Visual Studio automatycznie tworzy te podkatalogi w ramach procesu kompilacji. Ponieważ wszystkie zestawy satelickie mają taką samą nazwę pliku, podkatalogi są używane do przechowywania poszczególnych zestawów satelickich specyficznych dla kultury, dopóki nie zostaną podpisane przy użyciu pary kluczy publicznych/prywatnych.

9. Osadź poszczególne pliki zasobów specyficznych dla kultury w celu opóźniania podpisanych zestawów satelickich i Zapisz je w odpowiednim katalogu. Polecenie to zrób dla każdego pliku Resources:

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    gdzie *Culture* jest nazwą kultury. W tym przykładzie nazwy kultur to en-US, fr-FR i ru-RU.

10. Podpisz StringLibrary. dll przy użyciu [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) w następujący sposób:

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. Ponowne podpisywanie poszczególnych zestawów satelickich. W tym celu należy użyć [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) w następujący sposób dla każdego zestawu satelickiego:

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. Zarejestruj StringLibrary. dll i każdy z jej zestawów satelickich w globalnej pamięci podręcznej zestawów przy użyciu następującego polecenia:

    ```console
    gacutil -i filename
    ```

    gdzie *filename* jest nazwą pliku do zarejestrowania.

13. Jeśli używasz programu Visual Studio, Utwórz nowy projekt **aplikacji konsoli** o nazwie `Example`, Dodaj odwołanie do StringLibrary. dll i Poniższy kod źródłowy, a następnie Skompiluj.

    [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    Aby skompilować z wiersza polecenia, użyj następującego polecenia dla C# kompilatora:

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    Wiersz polecenia dla kompilatora Visual Basic jest:

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. Uruchom przykład. exe.

## <a name="see-also"></a>Zobacz także

- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
- [Opóźnione podpisywanie zestawu](../../standard/assembly/delay-sign.md)
- [Al.exe (konsolidator zestawów)](../tools/al-exe-assembly-linker.md)
- [Sn.exe (narzędzie silnych nazw)](../tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
- [Zasoby w aplikacjach klasycznych](index.md)
