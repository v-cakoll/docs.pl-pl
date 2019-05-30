---
title: 'Środki zaradcze: Wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8811fd916afcb39c466b8c9a60f7c7ed2a62ea8
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301433"
---
# <a name="mitigation-product-versioning"></a>Środki zaradcze: Wersjonowanie produktu
W .NET Framework 4.6 lub nowszy przechowywanie wersji produktu została zmieniona z poprzednich wersji programu .NET Framework (.NET Framework 4, 4.5, 4.5.1 i 4.5.2).  
  
## <a name="product-versioning-changes"></a>Zmiany wersji produktu  
 Poniżej przedstawiono szczegółowe zmiany:  
  
- Wartość `Version` wpis `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucz został zmieniony na `4.6.` *xxxxx* dla programu .NET Framework 4.6 i jego wydania punktowe i `4.7.` *xxxxx* dla. .NET Framework 4.7. W .NET Framework 4.5, 4.5.1 i 4.5.2, miał format `4.5.` *xxxxx*.  
  
- Wersji plików i produktów w przypadku plików .NET Framework została zmieniona z wcześniejszej schemat przechowywania wersji `4.0.30319.x` do `4.6.X.0` dla programu .NET Framework 4.6 i jego wydania punktowe i `4.7.X.0` dla programu .NET Framework 4.7 i jego punktu wydania. Możesz zobaczyć te nowe wartości, podczas wyświetlania pliku **właściwości** po prawym przyciskiem myszy w pliku.  
  
- <xref:System.Reflection.AssemblyFileVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybuty dla zestawów zarządzanych ma <xref:System.Version> wartości w formularzu `4.6.X.0` dla programu .NET Framework 4.6 i jego wydania punktowe, i `4.7.X.0` dla programu .NET Framework 4.7.  
  
- W programie .NET Framework 4.6, 4.6.1 i 4.6.2 oraz 4.7 <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca ciąg wersji Naprawiono `4.0.30319.42000`. W .NET Framework 4, 4.5, 4.5.1 i 4.5.2, zwraca ciągi wersji w formacie `4.0.30319.xxxxx` (na przykład "4.0.30319.18010"). Należy pamiętać, że nie zaleca się kod aplikacji, biorąc wszelkie nowe zależności <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="handling-the-product-versioning-changes"></a>Obsługa zmiany wersji produktu  
 Ogólnie rzecz biorąc należy zależne aplikacje zalecane techniki wykrywania takich zadań jak wersję środowiska uruchomieniowego programu .NET Framework i katalog instalacyjny:  
  
- Aby wykryć wersji środowiska uruchomieniowego programu .NET Framework, zobacz [jak: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
- Aby określić ścieżkę instalacji dla programu .NET Framework, należy użyć wartości `InstallPath` wpis `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucza.  
  
    > [!IMPORTANT]
    >  Jest nazwą podklucza `NET Framework Setup`, a nie `.NET Framework Setup`.  
  
- Aby określić ścieżkę katalogu do .NET Framework środowisko uruchomieniowe języka wspólnego, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metody.  
  
- Aby uzyskać wersję środowiska CLR, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metody.   Dla programu .NET Framework 4 i jego punktu zwalnia (.NET Framework 4.5, 4.5.1, 4.5.2 i .NET Framework 4.6, 4.6.1, 4.6.2 i 4.7), zwraca ciąg `v4.0.30319`.  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
