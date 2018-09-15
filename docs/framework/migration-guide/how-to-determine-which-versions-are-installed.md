---
title: 'Porady: Określanie, które wersje programu .NET Framework są zainstalowane.'
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649500"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Porady: Określanie, które wersje programu .NET Framework są zainstalowane.

Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach. Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika. Należy zwrócić uwagę na to, że .NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:  
  
-   Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji. .NET Framework i zestawy współużytkują ten sam numer wersji.  
  
-   Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji. Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Aby uzyskać dokładne listę wersji programu .NET Framework zainstalowana na komputerze, można wyświetlić rejestr lub wykonaj zapytanie dotyczące rejestru w kodzie:  
  
 [Wyświetlanie w rejestrze (wersje 1 – 4)](#net_a)  
 [Wyświetlanie w rejestrze (w wersji 4.5 lub nowszy)](#net_b)  
 [Wykonaj zapytanie dotyczące rejestru (wersje 1 – 4) za pomocą kodu](#net_c)  
 [Wykonaj zapytanie dotyczące rejestru (w wersji 4.5 lub nowszy) za pomocą kodu](#net_d)  
 [Przy użyciu programu PowerShell do wykonywania zapytań w rejestrze (w wersji 4.5 lub nowszy)](#ps_a)  
  
 Aby znaleźć wersję środowiska CLR, można użyć narzędzia lub kodu:  
  
 [Za pomocą narzędzia Clrver](#clr_a)  
 [Aby wysłać zapytanie klasy System.Environment przy użyciu kodu](#clr_b)  
  
 Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: ustalić Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Aby uzyskać informacje o instalowaniu programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Aby znaleźć wersji programu .NET Framework, wyświetlając rejestru (.NET Framework 1 – 4)  
  
1.  Na **Start** menu, wybierz **Uruchom**.  
  
2.  W **Otwórz** wprowadź **regedit.exe**.  
  
     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.  
  
3.  W Edytorze rejestru otwórz następujący podklucz:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Zainstalowane wersje są wymienione w podkluczu NDP. Numer wersji jest przechowywany w **wersji** wpisu. Aby uzyskać [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **wersji** wpis jest klient lub pełny podklucz (pod NDP) lub w obu tych podkluczach.  
  

    > [!NOTE]
    > Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Aby znaleźć wersji programu .NET Framework, wyświetlając rejestru (.NET Framework 4.5 i nowsze)

1. Na **Start** menu, wybierz **Uruchom**.

2. W **Otwórz** wprowadź **regedit.exe**.

     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.

3. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Należy pamiętać, że ścieżka do `Full` podklucz obejmuje podklucz `Net Framework` zamiast `.NET Framework`.

    > [!NOTE]
    > Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.

     Wyszukaj wartość DWORD o nazwie `Release`. Istnienie `Release` DWORD oznacza, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej, została zainstalowana na tym komputerze.

     ![Wpis rejestru dla programu .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Wartość `Release` typu DWORD wskazuje, która wersja programu .NET Framework jest zainstalowana.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Wartość DWORD dotycząca wersji|Wersja|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|.NET framework 4.5.1 zainstalowaną w systemie Windows 8.1 lub Windows Server 2012 R2|
    |378758|.NET framework 4.5.1, w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2|
    |379893|.NET Framework 4.5.2|
    |Tylko w systemach Windows 10: 393295<br /><br /> W innych wersjach systemu operacyjnego: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |Tylko w systemach Windows 10 Listopadową aktualizacją: 394254<br /><br /> W innych wersjach systemu operacyjnego: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |W Rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802<br /><br /> W innych wersjach systemu operacyjnego: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |W systemie Windows 10 dla twórców tylko zaktualizować: 460798<br/><br/> W innych wersjach systemu operacyjnego: 460805 | .NET framework 4.7 |
    |Na Windows 10 Fall Creators Update tylko: 461308<br/><br/> W innych wersjach systemu operacyjnego: 461310 | .NET Framework 4.7.1 |
    |W usłudze Windows Update 10 kwietnia 2018 r. tylko: 461808<br/><br/> W innych wersjach systemu operacyjnego: 461814| .NET framework 4.7.2 |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>Można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 1 – 4)

- Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby dostęp do podklucza Software\Microsoft\NET Framework Setup\NDP\ w kluczu HKEY_LOCAL_MACHINE w rejestrze systemu Windows.

     Poniższy kod przedstawia przykład tego zapytania.

    > [!NOTE]
    > Ten kod nie pokazuje, jak wykrywać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej. Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji. Dla kodu, który wykrywa [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsze wersje, zobacz następną sekcję w tym artykule.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     W przykładzie są generowane dane wyjściowe podobne do następujących:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>Można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)

1. Istnienie `Release` typu DWORD wskazuje, że na komputerze zainstalowano .NET Framework 4.5 lub nowszej. Wartość słowa kluczowego wskazuje zainstalowanej wersji. Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby dostęp do podklucza Software\Microsoft\NET Framework setup\ndp\v4\full ma w kluczu HKEY_LOCAL_MACHINE w rejestrze systemu Windows.

2. Sprawdź wartość `Release` słowo kluczowe, aby ustalić zainstalowaną wersję. Być zgodne, można sprawdzić wartość większa niż lub równa wartości wymienione w tabeli. Poniżej przedstawiono wersje programu .NET Framework i skojarzone `Release` słów kluczowych.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Wersja|Wartość DWORD dotycząca wersji|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET framework 4.5.1 zainstalowane z Windows 8.1|378675|
    |.NET framework 4.5.1, w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2|378758|
    |.NET Framework 4.5.2|379893|
    |.NET framework 4.6 zainstalowane z systemem Windows 10|393295|
    |.NET framework 4.6 zainstalowany w innych wersjach systemu operacyjnego Windows|393297|
    |Program .NET framework 4.6.1 zainstalowane w systemie Windows 10|394254|
    |Program .NET framework 4.6.1 zainstalowany w innych wersjach systemu operacyjnego Windows|394271|
    |.NET framework 4.6.2 w systemie Rocznicowa aktualizacja systemu Windows 10 i Windows Server 2016|394802|
    |.NET framework 4.6.2 zainstalowany w innych wersjach systemu operacyjnego Windows|394806|
    |.NET framework 4.7 zainstalowanym systemem Windows 10 Creators Update|460798|
    |.NET framework 4.7 zainstalowany w innych wersjach systemu operacyjnego Windows|460805|
    |.NET framework 4.7.1 w systemie Windows 10 Fall Creators Update|461308|
    |.NET framework 4.7.1 zainstalowany w innych wersjach systemu operacyjnego Windows|461310|
    |.NET framework 4.7.2 zainstalowany w systemie Windows 10 kwietnia 2018 r. Zaktualizuj|461808|
    |.NET framework 4.7.2 zainstalowany w innych wersjach systemu operacyjnego Windows|461814|
    
     Następujące testy przykład `Release` wartości w rejestrze, aby określić, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsza wersja programu .NET Framework jest zainstalowana.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     W tym przykładzie następuje zalecana praktyka dla kontroli wersji:

    - Sprawdza, czy wartość `Release` wpis jest *większa lub równa* wartości kluczy znanych wydania.

    - Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>Aby sprawdzić, czy są minimalna wymagana wersja programu .NET Framework, wykonując zapytanie w rejestrze w programie PowerShell (.NET Framework 4.5 i nowsze)

- Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy platformy .NET Framework 4.6.2 lub nowszy jest zainstalowany, niezależnie od wersji systemu operacyjnego Windows (zwracanie `True` , gdy jest i `False` inaczej).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Możesz zastąpić `394802` w poprzednim przykładzie, za pomocą innej wartości z poniższej tabeli, aby sprawdzić, czy są dostępne różne minimalna wymagana wersja programu .NET Framework.
  
    |Wersja|Minimalna wartość DWORD wydania|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |.NET framework 4.7|460798|
    |.NET Framework 4.7.1|461308|
    |.NET framework 4.7.2|461808|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Aby znaleźć bieżącą wersję środowiska uruchomieniowego za pomocą narzędzia Clrver

- Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.

     Z wiersza polecenia Visual Studio, wprowadź `clrver`. To polecenie tworzy dane wyjściowe podobne do poniższych:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Aby znaleźć bieżącą wersję środowiska uruchomieniowego, badając klasę Environment w kodzie

- Zapytanie <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu, który identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Możesz użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji głównej (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji pomocniczej (na przykład, "0" do wersji 4.0 lub nowszej), lub <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby uzyskać całą wersję ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie). Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Właściwość nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.

     Dla platformy .NET Framework 4, 4.5, 4.5.1 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Version> obiektu, którego reprezentacja ciągu ma postać `4.0.30319.xxxxx`. Dla programu .NET Framework 4.6 lub nowszy, ma on postać `4.0.30319.42000`.

    > [!IMPORTANT]
    > Aby uzyskać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszym, nie zaleca się przy użyciu <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska uruchomieniowego. Zamiast tego zaleca się zapytania rejestru zgodnie z opisem w [można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)](#net_d) sekcji we wcześniejszej części tego artykułu.

     Poniżej przedstawiono przykład zapytania dotyczącego <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości, aby uzyskać informacje o wersji środowiska uruchomieniowego:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     W przykładzie są generowane dane wyjściowe podobne do następujących:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Zobacz także

[Instrukcje: określanie, które aktualizacje programu .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)  
[Wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)  
