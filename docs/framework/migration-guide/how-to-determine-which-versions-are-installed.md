---
title: Określanie, które wersje programu .NET Framework są zainstalowane
description: Użyj kodu, regedit. exe lub PowerShell, aby wykryć, które wersje .NET Framework są zainstalowane na komputerze, badając rejestr systemu Windows.
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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093837"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Instrukcje: Określanie, które wersje .NET Framework są zainstalowane

Użytkownicy mogą [instalować](../install/index.md) i uruchamiać wiele wersji .NET Framework na swoich komputerach. Podczas opracowywania lub wdrażania aplikacji może być konieczne, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze użytkownika. Rejestr zawiera listę wersji .NET Framework zainstalowanych na komputerze.

.NET Framework składa się z dwóch głównych składników, które są osobno dla wersji:

- Zestaw zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji. .NET Framework i zestawy mają ten sam numer wersji. Na przykład .NET Framework wersje obejmują 4,5, 4.6.1 i 4.7.2.

- Środowisko uruchomieniowe języka wspólnego (CLR), które zarządza kodem aplikacji i go wykonuje. Jedna wersja środowiska CLR obsługuje zazwyczaj wiele wersji .NET Framework. Na przykład środowisko CLR w wersji 4.0.30319. *XXXXX* , gdzie *XXXXX* jest mniejszy niż 42000, obsługuje .NET Framework wersji 4 do 4.5.2. Wersja środowiska CLR o wartości większej lub równej 4.0.30319.42000 obsługuje wersje .NET Framework począwszy od .NET Framework 4,6.

Narzędzia obsługiwane przez społeczność są dostępne, aby pomóc w wykrywaniu, które wersje .NET Framework są zainstalowane:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Narzędzie wiersza polecenia programu .NET 2,0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Moduł programu PowerShell 2,0.

Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji .NET Framework, zobacz [How to: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Wykryj .NET Framework 4,5 i nowsze wersje

Wersja .NET Framework (4,5 lub nowsza) zainstalowana na komputerze jest wymieniona w rejestrze w **HKEY_LOCAL_MACHINE\\oprogramowanie\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Jeśli brakuje **pełnego** podklucza, to .NET Framework 4,5 lub nowsze nie są zainstalowane.

> [!NOTE]
> Podklucz **instalacji programu .NET Framework** w ścieżce rejestru *nie* zaczyna się od kropki.

Wartość REG_DWORD **wydania** w rejestrze reprezentuje wersję zainstalowanej .NET Framework.

<a name="version_table"></a>

| Wersja programu .NET Framework | Wartość **wydania** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Wszystkie systemy operacyjne Windows: 378389 |
| .NET Framework 4.5.1   | W systemach Windows 8.1 i Windows Server 2012 R2:378675<br />We wszystkich innych systemach operacyjnych Windows: 378758 |
| .NET Framework 4.5.2   | Wszystkie systemy operacyjne Windows: 379893 |
| Program .NET Framework 4.6     | W systemie Windows 10:393295<br />We wszystkich innych systemach operacyjnych Windows: 393297 |
| .NET Framework 4.6.1   | W systemach aktualizacji systemu Windows 10 listopad: 394254<br />We wszystkich innych systemach operacyjnych Windows (w tym Windows 10): 394271 |
| .NET Framework 4.6.2   | W rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802<br />Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 394806 |
| .NET framework 4.7     | Aktualizacja systemu Windows 10 dla twórców: 460798<br />Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 460805 |
| .NET Framework 4.7.1   | W przypadku aktualizacji systemu Windows 10 dla twórców i systemu Windows Server w wersji 1709:461308<br/>Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 461310 |
| .NET Framework 4.7.2   | W systemie Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461808<br/>We wszystkich systemach operacyjnych Windows innych niż Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461814 |
| .NET Framework 4,8     | W systemie Windows 10 maja 2019 Update i aktualizacja Windows 10 listopad 2019:528040<br/>W systemach Windows 10 i Windows Server, wersja 1909:528209<br/>Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 528049 |

### <a name="minimum-version"></a>Wersja minimalna

Aby określić, czy jest dostępna *minimalna* wersja .NET Framework, użyj najmniejszej wartości REG_DWORD **wydania** dla tej wersji z poprzedniej tabeli.

Na przykład, jeśli aplikacja działa w .NET Framework 4,8 lub nowszej wersji, należy sprawdzić, **czy w wersji REG_DWORD wartość** jest *większa niż lub równa* 528040.

| Wersja programu .NET Framework | Wartość minimalna |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| Program .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
| .NET Framework 4.7.2   | 461808 |
| .NET Framework 4,8     | 528040 |

### <a name="use-registry-editor"></a>Korzystanie z edytora rejestru

01. Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.

    Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.

01. W Edytorze rejestru Otwórz następujący podklucz: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Jeśli **pełny** podklucz nie jest obecny, nie masz zainstalowanego .NET Framework 4,5 lub nowszego.

01. Sprawdź, czy REG_DWORD wpis o nazwie **Release**. Jeśli istnieje, jest zainstalowana .NET Framework 4,5 lub nowsza. Jego wartość odnosi się do określonej wersji .NET Framework. Na przykład, wartość wpisu **zlecenia** to 528040, który jest kluczem wydania dla .NET Framework 4,8.

    ![Wpis rejestru dla .NET Framework 4,5](./media/clr-installdir.png "Wpis rejestru dla .NET Framework 4,5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Sprawdzanie minimalnej wersji przy użyciu programu PowerShell

Użyj poleceń programu PowerShell, aby sprawdzić wartość wpisu **wydania** **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\pełnego** podklucza.

Poniższe przykłady umożliwiają sprawdzenie wartości wpisu **wydania** , aby określić, czy .NET Framework 4.6.2 lub nowszy. Ten kod zwraca `True`, jeśli jest zainstalowany i `False` w przeciwnym razie.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Tworzenie zapytań dotyczących rejestru przy użyciu kodu

01. Użyj metod <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\NET Framework Setup\\NDP\\v4\\pełnego** podklucza w rejestrze systemu Windows.

    > [!IMPORTANT]
    > Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wymienione wcześniej. Rejestr 64-bitowy jest dostępny w **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\** podklucza. Na przykład podklucz rejestru dla .NET Framework 4,5 jest **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\zapełnić**.

01. Sprawdź wartość REG_DWORD **wydania** , aby określić zainstalowaną wersję. Aby można było przesłać dalej, sprawdź, czy wartość jest większa niż lub równa wartości wymienionej w [tabeli wersji .NET Framework](#version_table).

Poniższy przykład sprawdza wartość wpisu **Release** w rejestrze, aby znaleźć .NET Framework 4,5 i nowsze wersje, które są zainstalowane:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Ten przykład jest zgodny z zalecaną metodą sprawdzania wersji:

- Sprawdza, czy wartość wpisu **wydania** jest *większa niż lub równa* wartości znanych kluczy wydania.
- Sprawdza w kolejności od najnowszej wersji do najwcześniejszej wersji.

## <a name="detect-net-framework-10-through-40"></a>Wykryj .NET Framework 1,0 do 4,0

Każda wersja .NET Framework od 1,1 do 4,0 jest wyświetlana jako podklucz w **HKEY_LOCAL_MACHINE\\oprogramowanie\\Microsoft\\NET Framework instalator\\NDP**. Poniższa tabela zawiera listę ścieżek do poszczególnych wersji .NET Framework. W przypadku większości wersji istnieje REG_DWORD wartość `1`, aby wskazać **, że ta** wersja jest zainstalowana. W tych podkluczach istnieje również **wersja** REG_SZ wartość, która zawiera ciąg wersji.

> [!NOTE]
> Podklucz **instalacji programu .NET Framework** w ścieżce rejestru *nie* zaczyna się od kropki.

| Wersja struktury  | Podklucz rejestru | Wartość |
| ------------------ | --------------- | ----- |
| 1.0                | **Oprogramowanie HKLM\\\\Microsoft\\. NETFramework\\\\1.0\\3705**     | **Zainstaluj** program REG_SZ równe `1` |
| 1.1                | **HKLM\\oprogramowania\\Microsoft\\NET Framework Setup\\NDP\\v 1.1.4322**   | **Zainstaluj** program REG_DWORD równe `1` |
| 2.0                | **HKLM\\oprogramowania\\Microsoft\\NET Framework Setup\\NDP\\v 2.0.50727**  | **Zainstaluj** program REG_DWORD równe `1` |
| 3.0                | **HKLM\\Software\\Instalator programu Microsoft\\.NET Framework\\NDP\\v 3.0\\Setup** | **InstallSuccess** REG_DWORD równe `1` |
| 3,5                | **HKLM\\oprogramowania\\Microsoft\\NET Framework Setup\\NDP\\v 3.5**        | **Zainstaluj** program REG_DWORD równe `1` |
| 4,0 profil klienta | **HKLM\\oprogramowania\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**  | **Zainstaluj** program REG_DWORD równe `1` |
| pełny profil 4,0   | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**    | **Zainstaluj** program REG_DWORD równe `1` |

> [!IMPORTANT]
> Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wymienione wcześniej. Rejestr 64-bitowy jest dostępny w **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\** podklucza. Na przykład podklucz rejestru dla .NET Framework 3,5 jest **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v 3.5**.

Zwróć uwagę, że ścieżka rejestru do podklucza .NET Framework 1,0 różni się od innych.

### <a name="use-registry-editor-older-framework-versions"></a>Użyj edytora rejestru (starsze wersje Framework)

01. Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.

    Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.

01. Otwórz podklucz pasujący do wersji, którą chcesz sprawdzić. Skorzystaj z tabeli w sekcji [wykrywanie .NET Framework 1,0 do 4,0](#detect-net-framework-10-through-40) .

    Na poniższej ilustracji przedstawiono podklucz i jego wartość **wersji** dla .NET Framework 3,5.

    ![Wpis rejestru dla .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 i wcześniejsze wersje")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Wykonywanie zapytania dotyczącego rejestru przy użyciu kodu (starsze wersje Framework)

Użyj klasy <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\NET Framework instalator\\NDP** podklucz w rejestrze systemu Windows.

> [!IMPORTANT]
> Jeśli uruchomiona aplikacja jest 32-bitowa i działa w 64-bitowym systemie Windows, ścieżki rejestru będą inne niż wymienione wcześniej. Rejestr 64-bitowy jest dostępny w **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\** podklucza. Na przykład podklucz rejestru dla .NET Framework 3,5 jest **HKEY_LOCAL_MACHINE\\oprogramowania\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v 3.5**.

Poniższy przykład umożliwia znalezienie zainstalowanych wersji .NET Framework od 1 do 4:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Znajdź wersje środowiska CLR

.NET Framework środowisko CLR zainstalowane z .NET Framework jest używane oddzielnie. Istnieją dwa sposoby wykrywania wersji .NET Framework CLR:

- **Narzędzie Clrver. exe**

  Użyj [Narzędzia wersji środowiska CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) , aby określić, które wersje środowiska CLR są zainstalowane na komputerze. Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md) i wprowadź `clrver`.

  Przykładowe dane wyjściowe:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **Klasa `Environment`**

  > [!IMPORTANT]
  > W przypadku .NET Framework 4,5 i nowszych wersji nie należy używać właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType> do wykrywania wersji środowiska CLR. Zamiast tego należy wykonać zapytanie dotyczące rejestru zgodnie z opisem w artykule [wykrywanie .NET Framework 4,5 i nowszych wersji](#detect-net-framework-45-and-later-versions).
  
  01. Zbadaj Właściwość <xref:System.Environment.Version?displayProperty=nameWithType>, aby pobrać obiekt <xref:System.Version>.
  
      Zwrócony obiekt `System.Version` identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogły zostać zainstalowane na komputerze.
  
      W przypadku .NET Framework w wersji 4, 4,5, 4.5.1 i 4.5.2 ciąg reprezentujący zwrócony obiekt <xref:System.Version> ma postać 4.0.30319. *XXXXX*, gdzie *XXXXX* jest mniejszy niż 42000. W przypadku .NET Framework 4,6 i nowszych wersje ma postać 4.0.30319.42000.
  
  01. Po utworzeniu obiektu **wersji** wykonaj zapytanie w następujący sposób:
  
      - Aby uzyskać informacje o głównym identyfikatorze wydania (na przykład *4* dla wersji 4,0), użyj właściwości <xref:System.Version.Major%2A?displayProperty=nameWithType>.
  
      - W przypadku pomocniczego identyfikatora wydania (na przykład *0* w przypadku wersji 4,0) użyj właściwości <xref:System.Version.Minor%2A?displayProperty=nameWithType>.
  
      - Dla całego ciągu wersji (na przykład *4.0.30319.18010*) użyj metody <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.

  W poniższym przykładzie zastosowano Właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> do pobrania informacji o wersji środowiska CLR:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md)
- [Zainstaluj .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [.NET Framework wersje i zależności](versions-and-dependencies.md)
