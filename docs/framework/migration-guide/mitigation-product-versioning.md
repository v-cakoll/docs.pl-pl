---
title: Środki zaradcze Przechowywanie wersji produktu
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91db9d8c6fccf75bc9025a9487517e8c55d016cc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779211"
---
# <a name="mitigation-product-versioning"></a>Środki zaradcze Przechowywanie wersji produktu

W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).

## <a name="product-versioning-changes"></a>Zmiany wersji produktu

Poniżej przedstawiono szczegółowe zmiany:

- Wartość `Version` wpisu `4.7.` `4.6.` w kluczu zmieniła się na XXXXX dla .NET Framework 4,6 i jego wydań punktów oraz do XXXXX dla .NET Framework 4,7. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.` *XXXXX*.

- Wersja plików i produktów dla plików .NET Framework zmieniła się ze schematu wcześniejszej wersji programu `4.0.30319.x` na `4.6.X.0` dla .NET Framework 4,6 i jego wydań `4.7.X.0` punktów, a w przypadku .NET Framework 4,7 i jego wydań punktów. Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.

- <xref:System.Version> `4.7.X.0` `4.6.X.0` Atrybuty i dla<xref:System.Reflection.AssemblyInformationalVersionAttribute> zestawów zarządzanych mają wartości w postaci dla .NET Framework 4,6 i jego wydań punktów oraz dla .NET Framework 4,7. <xref:System.Reflection.AssemblyFileVersionAttribute>

- Począwszy od .NET Framework 4,6, <xref:System.Environment.Version%2A?displayProperty=nameWithType> Właściwość zwraca ciąg `4.0.30319.42000`stałej wersji. W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie `4.0.30319.xxxxx` , gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010"). Należy pamiętać, że kod aplikacji nie jest zalecany we <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.

### <a name="handling-the-product-versioning-changes"></a>Obsługa zmian wersji produktu

Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:

- Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Ustal, które wersje .NET Framework są](how-to-determine-which-versions-are-installed.md)zainstalowane.

- Aby określić ścieżkę instalacji .NET Framework, użyj wartości `InstallPath` wpisu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` w kluczu.

  > [!IMPORTANT]
  > Nazwa podklucza `NET Framework Setup`to, `.NET Framework Setup`nie.

- Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodę.

- Aby uzyskać wersję środowiska CLR, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodę.   W przypadku .NET Framework 4 i jego wydań (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca ciąg `v4.0.30319`.

## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](runtime-changes-in-the-net-framework-4-6.md)
