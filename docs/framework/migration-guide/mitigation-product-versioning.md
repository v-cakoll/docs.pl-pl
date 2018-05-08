---
title: 'Ograniczenie: wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 483a6532ad62fb7e1561ac5cc4de37aeaaf45fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-product-versioning"></a>Ograniczenie: wersjonowanie produktu
W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i nowszych wersji produktu został zmieniony z poprzednich wersji programu .NET Framework (.NET Framework 4, 4.5.1, 4.5 i 4.5.2).  
  
## <a name="product-versioning-changes"></a>Zmiany wersji produktu  
 Poniżej przedstawiono szczegółowe zmiany:  
  
-   Wartość `Version` wpis w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucz został zmieniony na `4.6.` *xxxxx* dla programu .NET Framework 4.6 i zwalnia jego punktu i do `4.7.` *xxxxx* dla. NET Framework 4.7. W programie .NET Framework 4.5 i 4.5.1, 4.5.2, miał format `4.5.` *xxxxx*.  
  
-   Przechowywanie wersji plików i produktu dla plików platformy .NET Framework został zmieniony z wcześniejszych wersji systemu `4.0.30319.x` do `4.6.X.0` dla programu .NET Framework 4.6 i zwalnia jego punktu i do `4.7.X.0` .NET Framework 4.7 i jego punktu wersjami. Można zobaczyć te nowe wartości, podczas wyświetlania pliku **właściwości** po prawym przyciskiem myszy plik.  
  
-   <xref:System.Reflection.AssemblyFileVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybuty dla zestawów zarządzanych ma <xref:System.Version> wartości w formularzu `4.6.X.0` dla programu .NET Framework 4.6 i jego wersje punktu i `4.7.X.0` dla .NET Framework 4.7.  
  
-   W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 i 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca ciąg wersji stałej `4.0.30319.42000`. W programie .NET Framework 4, 4.5.1, 4.5 i 4.5.2, zwraca ciągów w formacie `4.0.30319.xxxxx` (na przykład "4.0.30319.18010"). Należy pamiętać, że nie zaleca się kod aplikacji, biorąc wszelkie nowe zależności <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="handling-the-product-versioning-changes"></a>Obsługa zmiany wersji produktu  
 Ogólnie rzecz biorąc aplikacje powinny zależą od zalecane techniki wykrywania czynności, takich jak wersja środowiska uruchomieniowego .NET Framework i katalog instalacji:  
  
-   Aby wykryć wersji środowiska uruchomieniowego .NET Framework, zobacz [porady: ustalić, które .NET Framework są zainstalowane wersje](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
-   Aby określić ścieżkę instalacji dla programu .NET Framework, użyj wartości `InstallPath` wpis w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucza.  
  
    > [!IMPORTANT]
    >  Nazwa podklucza jest `NET Framework Setup`, a nie `.NET Framework Setup`.  
  
-   Aby określić ścieżkę katalogu do .NET Framework środowisko uruchomieniowe języka wspólnego, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metody.  
  
-   Aby pobrać wersji środowiska CLR, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metody.   Dla programu .NET Framework 4 i jego punktu zwalnia (.NET Framework 4.5, 4.5.1, 4.5.2, i [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 i 4.7), zwraca ciąg `v4.0.30319`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
