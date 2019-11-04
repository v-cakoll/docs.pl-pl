---
title: 'Ograniczenie: wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457823"
---
# <a name="mitigation-product-versioning"></a>Ograniczenie: wersjonowanie produktu

W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).

## <a name="product-versioning-changes"></a>Zmiany wersji produktu

Poniżej przedstawiono szczegółowe zmiany:

- Wartość wpisu `Version` w kluczu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` została zmieniona na `4.6.`*XXXXX* dla .NET Framework 4,6 i jego wydań punktów oraz `4.7.`*xxxxx* dla .NET Framework 4,7. W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.`*XXXXX*.

- Wersje plików i produktów dla plików .NET Framework zmieniły się ze schematu wcześniejszej wersji `4.0.30319.x` do `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a `4.7.X.0` .NET Framework 4,7 i jego wydania punktów. Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.

- Atrybuty <xref:System.Reflection.AssemblyFileVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> dla zestawów zarządzanych mają <xref:System.Version> wartości w postaci `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a `4.7.X.0` .NET Framework 4,7.

- Począwszy od .NET Framework 4,6, właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> zwraca ciąg stałej wersji `4.0.30319.42000`. W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie `4.0.30319.xxxxx` gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010"). Należy pamiętać, że kod aplikacji nie jest zalecany we właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType>.

### <a name="handling-the-product-versioning-changes"></a>Obsługa zmian wersji produktu

Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:

- Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).

- Aby określić ścieżkę instalacji .NET Framework, użyj wartości wpisu `InstallPath` w kluczu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.

  > [!IMPORTANT]
  > Nazwa podklucza jest `NET Framework Setup`, a nie `.NET Framework Setup`.

- Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj metodę <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.

- Aby uzyskać wersję środowiska CLR, wywołaj metodę <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.   W przypadku .NET Framework 4 i jego wydań punktów (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca `v4.0.30319`ciąg.

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
