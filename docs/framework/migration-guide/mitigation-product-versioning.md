---
title: 'Ograniczenie: wersjonowanie produktu'
description: W tym artykule dowiesz się, jak .NET Framework 4,6 i nowsze wersje produktu zmieniły się z poprzednich wersji.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475401"
---
# <a name="mitigation-product-versioning"></a>Ograniczenie: wersjonowanie produktu

W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).

## <a name="product-versioning-changes"></a>Zmiany wersji produktu

Poniżej przedstawiono szczegółowe zmiany:

- Wartość `Version` wpisu w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu zmieniła się na `4.6.` *XXXXX* dla .NET Framework 4,6 i jego wydań punktów oraz do `4.7.` *XXXXX* dla .NET Framework 4,7. W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.` *XXXXX*.

- Wersja plików i produktów dla plików .NET Framework zmieniła się ze schematu wcześniejszej wersji programu `4.0.30319.x` na `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a w `4.7.X.0` przypadku .NET Framework 4,7 i jego wydań punktów. Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.

- <xref:System.Reflection.AssemblyFileVersionAttribute>Atrybuty i <xref:System.Reflection.AssemblyInformationalVersionAttribute> dla zestawów zarządzanych mają <xref:System.Version> wartości w postaci `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów oraz `4.7.X.0` dla .NET Framework 4,7.

- Począwszy od .NET Framework 4,6, <xref:System.Environment.Version%2A?displayProperty=nameWithType> Właściwość zwraca ciąg stałej wersji `4.0.30319.42000` . W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie, `4.0.30319.xxxxx` gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010"). Należy pamiętać, że kod aplikacji nie jest zalecany we <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.

### <a name="handling-the-product-versioning-changes"></a>Obsługa zmian wersji produktu

Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:

- Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).

- Aby określić ścieżkę instalacji .NET Framework, użyj wartości `InstallPath` wpisu w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu.

  > [!IMPORTANT]
  > Nazwa podklucza to `NET Framework Setup` , nie `.NET Framework Setup` .

- Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodę.

- Aby uzyskać wersję środowiska CLR, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodę.   W przypadku .NET Framework 4 i jego wydań (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca ciąg `v4.0.30319` .

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
