---
title: "Ograniczenie: Ścieżka normalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e30099e315f88bd051dca2e1f6c83d1bccc49569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-normalization"></a>Ograniczenie: Ścieżka normalizacji
Począwszy od aplikacji docelowej [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w programie .NET Framework.  
  
## <a name="what-is-path-normalization"></a>Co to jest ścieżka normalizacji?  
 Normalizacji ścieżki pociąga za sobą modyfikowanie ciąg, który określa ścieżkę lub plików, dzięki czemu odpowiada prawidłową ścieżkę na docelowy system operacyjny. Normalizacji zwykle obejmuje:  
  
-   Kanoniczną separatory składnika i katalogu.  
  
-   Stosowanie bieżący katalog do ścieżki względnej.  
  
-   Ocena względna katalogu (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.  
  
-   Przycinanie określonych znaków.  
  
## <a name="the-changes"></a>Zmiany  
 Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w następujący sposób:  
  
-   Środowisko uruchomieniowe różni się do systemu operacyjnego [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) funkcji normalizacji ścieżki.  
  
-   Normalizacji nie obejmuje przycinanie końca katalogu segmenty (na przykład miejsca na końcu nazwy katalogu).  
  
-   Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` i dla interfejsów API We/Wy plików w bibliotece mscorlib.dll, `\\?\`.  
  
-   Środowisko uruchomieniowe nie można zweryfikować ścieżki składni urządzeń.  
  
-   Użycie składni urządzenia do dostępu alternatywne strumienie danych jest obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 W przypadku aplikacji, które odnoszą się do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub później, zmiany te są domyślnie. Powinny one zwiększyć wydajność zezwalając metod dostępu wcześniej niedostępny ścieżki do.  
  
 Aplikacje, które odnoszą się do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i wcześniejszych wersji, ale są uruchomione w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszy nie ma wpływu na tę zmianę.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aplikacje, które odnoszą się do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można zrezygnować z tej zmiany i użyć starszego normalizacji, dodając następujące polecenie, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Aplikacje, które odnoszą się do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub wcześniej, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji. plik konfiguracji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
