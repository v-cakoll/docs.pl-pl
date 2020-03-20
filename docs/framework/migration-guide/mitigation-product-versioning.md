---
title: 'Ograniczenie: wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457823"
---
# <a name="mitigation-product-versioning"></a>Ograniczenie: wersjonowanie produktu

W .NET Framework 4.6 i nowszych wersjach produktu została zmieniona z poprzednich wersji programu .NET Framework (.NET Framework 4, 4.5, 4.5.1 i 4.5.2).

## <a name="product-versioning-changes"></a>Zmiany wersji produktu

Poniżej przedstawiono szczegółowe zmiany:

- Wartość wpisu `Version` w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu została `4.6.`zmieniona na *xxxxx* dla .NET Framework 4.6 i jego wydania punktowe oraz `4.7.` *xxxxx* dla .NET Framework 4.7. W .NET Framework 4.5, 4.5.1 i 4.5.2 `4.5.`miał format *xxxxx*.

- Przechowywanie wersji plików i produktów dla plików .NET Framework zostało `4.0.30319.x` `4.6.X.0` zmienione z wcześniejszego schematu przechowywania wersji na program `4.7.X.0` .NET Framework 4.6 i jego wersje punktowe oraz na platformie .NET Framework 4.7 i jego wydaniach punktowych. Te nowe wartości można zobaczyć podczas wyświetlania **właściwości** pliku po kliknięciu prawym przyciskiem myszy na pliku.

- <xref:System.Reflection.AssemblyFileVersionAttribute> Atrybuty <xref:System.Reflection.AssemblyInformationalVersionAttribute> i dla zestawów zarządzanych mają <xref:System.Version> wartości w formularzu `4.6.X.0` dla programu .NET `4.7.X.0` Framework 4.6 i jego wersji punktowych oraz dla programu .NET Framework 4.7.

- Począwszy od programu .NET Framework <xref:System.Environment.Version%2A?displayProperty=nameWithType> 4.6, `4.0.30319.42000`właściwość zwraca ciąg wersji stałej . W .NET Framework 4, 4.5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie, `4.0.30319.xxxxx` w którym `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010"). Należy zauważyć, że nie zaleca się kod <xref:System.Environment.Version%2A?displayProperty=nameWithType> aplikacji przy żadnej nowej zależności od właściwości.

### <a name="handling-the-product-versioning-changes"></a>Obsługa zmian wersji produktu

Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich rzeczy, jak wersja środowiska wykonawczego programu .NET Framework i katalog instalacyjny:

- Aby wykryć wersję środowiska uruchomieniowego programu .NET Framework, zobacz [Jak: Określanie zainstalowanych wersji programu .NET Framework](how-to-determine-which-versions-are-installed.md).

- Aby określić ścieżkę instalacji dla programu .NET Framework, należy użyć wartości wpisu `InstallPath` w kluczu. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

  > [!IMPORTANT]
  > Nazwa podklucza `NET Framework Setup` `.NET Framework Setup`to , nie .

- Aby określić ścieżkę katalogu do środowiska uruchomieniowego <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> języka wspólnego programu .NET Framework, należy wywołać metodę.

- Aby uzyskać wersję CLR, <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> wywołaj metodę.   W przypadku programu .NET Framework 4 i jego wersji punktowych (.NET Framework 4.5, 4.5.1, 4.5.2 i .NET Framework 4.6, 4.6.1, `v4.0.30319`4.6.2 i 4.7) zwraca ciąg .

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
