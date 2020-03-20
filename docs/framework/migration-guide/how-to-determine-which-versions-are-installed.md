---
title: Określanie, które wersje programu .NET Framework są zainstalowane
description: Użyj kodu, regedit.exe lub programu PowerShell, aby wykryć, które wersje programu .NET Framework są zainstalowane na komputerze, przecząc rejestr systemu Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093837"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Jak: Określ, które wersje programu .NET Framework są zainstalowane

Użytkownicy mogą [instalować](../install/index.md) i uruchamiać wiele wersji programu .NET Framework na swoich komputerach. Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika. Rejestr zawiera listę wersji programu .NET Framework zainstalowanych na komputerze.

.NET Framework składa się z dwóch głównych składników, które są wersjonowane oddzielnie:

- Zestaw zestawów, które są kolekcje typów i zasobów, które zapewniają funkcje dla aplikacji. .NET Framework i zestawy współużytkują ten sam numer wersji. Na przykład wersje programu .NET Framework zawierają wersje 4.5, 4.6.1 i 4.7.2.

- Środowisko wykonawcze języka wspólnego (CLR), który zarządza i wykonuje kod aplikacji. Pojedyncza wersja CLR zazwyczaj obsługuje wiele wersji programu .NET Framework. Na przykład CLR w wersji 4.0.30319. *xxxxx* gdzie *xxxxx* jest mniejszy niż 42000, obsługuje .NET Framework w wersjach od 4 do 4.5.2. Wersja CLR większa lub równa wersji 4.0.30319.42000 obsługuje wersje programu .NET Framework, począwszy od programu .NET Framework 4.6.

Dostępne są narzędzia obsługiwane przez społeczność, które pomagają wykryć, które wersje programu .NET Framework są zainstalowane:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Narzędzie wiersza polecenia .NET 2.0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Moduł programu PowerShell 2.0.

Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [Jak: Określanie zainstalowanych aktualizacji programu .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Wykrywanie wersji programu .NET Framework 4.5 i nowszych

Wersja programu .NET Framework (4.5 i nowsza) zainstalowana na komputerze jest wymieniona w rejestrze w **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Jeśli brakuje **pełnego** klucza, program .NET Framework 4.5 lub wyższy nie jest zainstalowany.

> [!NOTE]
> Podklucz **Instalatora programu NET Framework** w ścieżce rejestru *nie* rozpoczyna się od okresu.

Wartość **REG_DWORD wydania** w rejestrze reprezentuje zainstalowaną wersję programu .NET Framework.

<a name="version_table"></a>

| Wersja programu .NET Framework | Wartość **wydania** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Wszystkie systemy operacyjne Windows: 378389 |
| .NET Framework 4.5.1   | W systemach Windows 8.1 i Windows Server 2012 R2: 378675<br />We wszystkich innych systemach operacyjnych Windows: 378758 |
| .NET Framework 4.5.2   | Wszystkie systemy operacyjne Windows: 379893 |
| Program .NET Framework 4.6     | W systemie Windows 10: 393295<br />We wszystkich innych systemach operacyjnych Windows: 393297 |
| .NET Framework 4.6.1   | W systemach Windows 10 November Update: 394254<br />We wszystkich innych systemach operacyjnych Windows (w tym Windows 10): 394271 |
| .NET Framework 4.6.2   | W systemie Windows 10 Anniversary Update i Windows Server 2016: 394802<br />We wszystkich innych systemach operacyjnych Windows (w tym w innych systemach operacyjnych Windows 10): 394806 |
| .NET Framework 4.7     | Aktualizacja dla twórców systemu Windows 10: 460798<br />We wszystkich innych systemach operacyjnych Windows (w tym w innych systemach operacyjnych Windows 10): 460805 |
| .NET Framework 4.7.1   | W systemie Windows 10 Fall Creators Update i Windows Server w wersji 1709: 461308<br/>We wszystkich innych systemach operacyjnych Windows (w tym w innych systemach operacyjnych Windows 10): 461310 |
|  .NET Framework 4.7.2   | W systemach Windows 10 April 2018 Update i Windows Server: wersja 1803: 461808<br/>We wszystkich systemach operacyjnych Windows innych niż Windows 10 April 2018 Update i Windows Server wersja 1803: 461814 |
|  .NET Framework 4.8     | W systemie Windows 10 May 2019 Update i Windows 10 Aktualizacja z listopada 2019: 528040<br/>W systemach Windows 10 i Windows Server w wersji 1909: 528209<br/>We wszystkich innych systemach operacyjnych Windows (w tym w innych systemach operacyjnych Windows 10): 528049 |

### <a name="minimum-version"></a>Minimalna wersja

Aby ustalić, czy *istnieje minimalna* wersja programu .NET Framework, należy użyć najmniejszej wartości **REG_DWORD wydania** dla tej wersji z poprzedniej tabeli.

Na przykład jeśli aplikacja działa w ramach .NET Framework 4.8 lub nowszej wersji, test **dla Release** REG_DWORD wartość, która jest większa *lub równa* 528040.

| Wersja programu .NET Framework | Wartość minimalna |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| Program .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
|  .NET Framework 4.7.2   | 461808 |
|  .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Korzystanie z Edytora rejestru

01. Z menu **Start** wybierz polecenie **Uruchom**, wprowadź *regedit*, a następnie wybierz **przycisk OK**.

    Aby uruchomić regedit, musisz mieć poświadczenia administracyjne.

01. W Edytorze rejestru otwórz następujący podklucz: **\\HKEY_LOCAL_MACHINE SOFTWARE\\Microsoft\\NET Framework Setup\\\\NDP v4\\Full**. Jeśli **podklucz Full** nie jest obecny, nie masz zainstalowany program .NET Framework 4.5 lub nowszych.

01. Sprawdź, czy REG_DWORD wpis o nazwie **Release**. Jeśli istnieje, masz zainstalowany program .NET Framework 4.5 lub nowszy. Jego wartość odpowiada określonej wersji programu .NET Framework. Na poniższej ilustracji, na przykład wartość **release** wpis jest 528040, który jest kluczem zwalniania dla .NET Framework 4.8.

    ![Wpis rejestru dla programu .NET Framework 4.5](./media/clr-installdir.png "Wpis rejestru dla programu .NET Framework 4.5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Sprawdzanie wersji minimalnej za pomocą programu PowerShell

Polecenia programu PowerShell za pomocą polecenia Programu PowerShell można sprawdzić wartość wpisu Wydania **HKEY_LOCAL_MACHINE\\software Microsoft NET Framework Setup NDP v4\\Full.Use\\\\\\\\** PowerShell commands to check the value of the **Release** entry of the HKEY_LOCAL_MACHINE SOFTWARE Microsoft NET Framework Setup NDP v4 Fullkey.

Poniższe przykłady sprawdź wartość **release** wpis, aby ustalić, czy .NET Framework 4.6.2 lub nowsze jest zainstalowany. Ten kod `True` zwraca, jeśli `False` jest zainstalowany i w inny sposób.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Kwerenda rejestru przy użyciu kodu

01. Użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metody, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\\OPROGRAMOWANIA\\Microsoft\\NET Framework Setup\\NDP\\v4\\Pełny** klucz w rejestrze systemu Windows.

    > [!IMPORTANT]
    > Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wcześniej wymienione. Rejestr 64-bitowy jest dostępny w podkluczy **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Na przykład podklucz rejestru dla programu .NET Framework 4.5 jest **HKEY_LOCAL_MACHINE\\\\\\\\SOFTWARE\\Wow6432Node Microsoft NET Framework Setup\\NDP\\v4 Full**.

01. Sprawdź wartość **release** REG_DWORD, aby określić zainstalowaną wersję. Aby być zgodnym z przyszłością, sprawdź, czy wartość jest większa lub równa wartości wymienionej w [tabeli wersji programu .NET Framework](#version_table).

Poniższy przykład sprawdza wartość **release** wpis w rejestrze, aby znaleźć .NET Framework 4.5 i nowsze wersje, które są zainstalowane:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

W tym przykładzie następuje zalecana praktyka sprawdzania wersji:

- Sprawdza, czy wartość **release** wpis jest *większa lub równa* wartości znanych kluczy zwalniania.
- Sprawdza w kolejności od najnowszej wersji do najwcześniejszej wersji.

## <a name="detect-net-framework-10-through-40"></a>Wykrywanie programu .NET Framework od 1,0 do 4,0

Każda wersja programu .NET Framework w zakresie od 1.1 do 4.0 jest wymieniona jako podklucz w **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**. W poniższej tabeli wymieniono ścieżkę do każdej wersji programu .NET Framework. W przypadku większości wersji istnieje **wartość install** REG_DWORD, `1` aby wskazać, że ta wersja jest zainstalowana. W tych podkluciach istnieje również **wartość version** REG_SZ, która zawiera ciąg wersji.

> [!NOTE]
> Podklucz **Instalatora programu NET Framework** w ścieżce rejestru *nie* rozpoczyna się od okresu.

| Wersja ramowa  | Podklucz rejestru | Wartość |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\\\Software\\Microsoft . Zasady\\\\NETFramework w wersji\\1.0 3705**     | **Instalacja** REG_SZ równa się`1` |
| 1.1                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NDP v1.1.4322**   | **Instalacja** REG_DWORD równa się`1` |
| 2.0                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NDP v2.0.50727**  | **Instalacja** REG_DWORD równa się`1` |
| 3.0                | **Instalator\\HKLM Software\\Microsoft\\NET Framework\\NDP\\w wersji 3.0\\** | **InstalacjaSukces** REG_DWORD równa się`1` |
| 3,5                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NDP v3.5**        | **Instalacja** REG_DWORD równa się`1` |
| 4.0 Profil klienta | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**  | **Instalacja** REG_DWORD równa się`1` |
| 4.0 Pełny profil   | **Oprogramowanie HKLM\\\\Microsoft\\\\NET\\Framework\\Setup NDP v4 Pełna**    | **Instalacja** REG_DWORD równa się`1` |

> [!IMPORTANT]
> Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wcześniej wymienione. Rejestr 64-bitowy jest dostępny w podkluczy **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Na przykład podklucz rejestru dla programu .NET Framework 3.5 jest **\\HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.

Należy zauważyć, że ścieżka rejestru do podklucza .NET Framework 1.0 różni się od innych.

### <a name="use-registry-editor-older-framework-versions"></a>Korzystanie z Edytora rejestru (starsze wersje frameworka)

01. Z menu **Start** wybierz polecenie **Uruchom**, wprowadź *regedit*, a następnie wybierz **przycisk OK**.

    Aby uruchomić regedit, musisz mieć poświadczenia administracyjne.

01. Otwórz podklucz odpowiadający wersji, którą chcesz sprawdzić. Użyj tabeli w sekcji [Detect .NET Framework 1.0 through 4.0.](#detect-net-framework-10-through-40)

    Na poniższej ilustracji przedstawiono podklucz i jego wartość **Version** dla programu .NET Framework 3.5.

    ![Wpis rejestru dla programu .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 i starsze wersje")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Kwerenda rejestru przy użyciu kodu (starsze wersje frameworka)

Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> tej klasy, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\\software\\Microsoft\\NET Framework Setup\\NDP** subkey w rejestrze systemu Windows.

> [!IMPORTANT]
> Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wcześniej wymienione. Rejestr 64-bitowy jest dostępny w podkluczy **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node.\\ ** Na przykład podklucz rejestru dla programu .NET Framework 3.5 jest **\\HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.

Poniższy przykład znajduje .NET Framework 1 do 4 wersje, które są zainstalowane:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Znajdź wersje CLR

Program .NET Framework CLR zainstalowany z programem .NET Framework jest wersjonatowany oddzielnie. Istnieją dwa sposoby wykrywania wersji programu CLR programu .NET Framework:

- **Narzędzie Clrver.exe**

  Użyj [narzędzia ClR Version (Clrver.exe),](../tools/clrver-exe-clr-version-tool.md) aby określić, które wersje programu CLR są zainstalowane na komputerze. Otwórz [wiersz polecenia dewelopera dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md) i wprowadź `clrver`.

  Przykładowe dane wyjściowe:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **Klasa `Environment`**

  > [!IMPORTANT]
  > Dla .NET Framework 4.5 i nowsze <xref:System.Environment.Version%2A?displayProperty=nameWithType> wersje nie należy używać właściwości do wykrywania wersji programu CLR. Zamiast tego należy zbadać rejestr zgodnie z opisem w [programie Detect .NET Framework 4.5 i nowszych wersjach](#detect-net-framework-45-and-later-versions).
  
  01. Kwerenda <xref:System.Environment.Version?displayProperty=nameWithType> właściwość, <xref:System.Version> aby pobrać obiekt.
  
      Zwrócony `System.Version` obiekt identyfikuje wersję środowiska wykonawczego, który jest obecnie wykonywany kod. Nie zwraca wersji zestawu lub innych wersji środowiska wykonawczego, które mogły zostać zainstalowane na komputerze.
  
      Dla .NET Framework w wersjach 4, 4.5, 4.5.1 i 4.5.2 reprezentacja ciągu zwróconego <xref:System.Version> obiektu ma formularz 4.0.30319. *xxxxx*, gdzie *xxxxx* jest mniejsza niż 42000. Dla .NET Framework 4.6 i nowszych wersji ma formularz 4.0.30319.42000.
  
  01. Po zakończeniu pracy w obiekcie **Version** należy zbadać go w następujący sposób:
  
      - Dla głównego identyfikatora wydania (na przykład *4* dla wersji 4.0), należy użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości.
  
      - Dla identyfikatora wersji pomocniczej (na przykład *0* dla wersji <xref:System.Version.Minor%2A?displayProperty=nameWithType> 4.0), należy użyć właściwości.
  
      - Dla całego ciągu wersji (na przykład *4.0.30319.18010*), użyj <xref:System.Version.ToString%2A?displayProperty=nameWithType> metody. Ta metoda zwraca pojedynczą wartość, która odzwierciedla wersję środowiska wykonawczego, który wykonuje kod. Nie zwraca wersji zestawu lub innych wersji środowiska wykonawczego, które mogą być zainstalowane na komputerze.

  W poniższym przykładzie <xref:System.Environment.Version%2A?displayProperty=nameWithType> użyto właściwości do pobierania informacji o wersji programu CLR:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Zobacz też

- [Jak: Określ, które aktualizacje programu .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Wersje i zależności programu .NET Framework](versions-and-dependencies.md)
