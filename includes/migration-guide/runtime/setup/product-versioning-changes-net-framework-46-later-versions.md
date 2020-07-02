---
ms.openlocfilehash: a5c6dda0c1d68468cd95f67716709dd059948c80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621337"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>Zmiany wersji produktu w .NET Framework 4,6 i nowszych wersjach

#### <a name="details"></a>Szczegóły

Wersja produktu zmieniła się z poprzednich wersji .NET Framework, a w szczególności z .NET Framework 4, 4,5, 4.5.1 i 4.5.2. Poniżej przedstawiono szczegółowe zmiany:<ul><li>Wartość <code>Version</code> wpisu w <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> kluczu zmieniła się na <code>4.6.xxxxx</code> dla .NET Framework 4,6 i jego wydań punktów oraz do <code>4.7.xxxxx</code> .NET Framework 4,7 i 4.7.1. W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format <code>4.5.xxxxx</code> .</li><li>Wersja plików i produktów dla plików .NET Framework zmieniła się ze schematu wcześniejszej wersji programu 4.0.30319. x na 4.6. X. 0 dla .NET Framework 4,6 i jego wydań punktów oraz do 4,7. X. 0 dla .NET Framework 4,7 i 4.7.1. Te nowe wartości są widoczne podczas przeglądania właściwości pliku po kliknięciu prawym przyciskiem myszy pliku.</li><li><xref:System.Reflection.AssemblyFileVersionAttribute>Atrybuty i <xref:System.Reflection.AssemblyInformationalVersionAttribute> dla zestawów zarządzanych mają wartości wersji w postaci 4.6. x. 0 dla .NET Framework 4,6 i jego wydań oraz 4,7. X. 0 dla .NET Framework 4,7 i 4.7.1.</li><li>W .NET Framework 4,6, 4.6.1, 4.6.2, 4,7 i 4.7.1 <xref:System.Environment.Version?displayProperty=nameWithType> Właściwość zwraca ciąg stałej wersji <code>4.0.30319.42000</code> . W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie <code>4.0.30319.xxxxx</code> (na przykład &quot; 4.0.30319.18010 &quot; ). Należy pamiętać, że kod aplikacji nie zaleca żadnej nowej zależności od właściwości Environment. Version.</li></ul>Aby uzyskać więcej informacji, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

#### <a name="suggestion"></a>Sugestia

Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:<ul><li>Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</li><li>Aby określić ścieżkę instalacji .NET Framework, użyj wartości <code>InstallPath</code> wpisu w <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> kluczu.</li></ul> <blockquote> [!IMPORTANT] Nazwa podklucza to <code>NET Framework Setup</code> , nie <code>.NET Framework Setup</code> .</blockquote> <ul><li>Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType> metodę.</li><li>Aby uzyskać wersję środowiska CLR, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType> metodę. W przypadku .NET Framework 4 i jego wydań punktów (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2, 4,7 i 4.7.1) zwraca ciąg v 4.0.30319.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
