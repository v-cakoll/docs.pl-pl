---
title: 'Środki zaradcze: Ścieżka normalizacji'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51291fbc9ad2927bc3b9649074a6dbf374aaf7f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648444"
---
# <a name="mitigation-path-normalization"></a>Środki zaradcze: Ścieżka normalizacji
Począwszy od aplikacji docelowej [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w programie .NET Framework.  
  
## <a name="what-is-path-normalization"></a>Co to jest ścieżka normalizacji?  
 Normalizowanie ścieżką obejmuje modyfikuje ciąg, który identyfikuje pliku lub ścieżki, tak aby odpowiada prawidłowej ścieżki, na docelowy system operacyjny. Normalizacja zwykle obejmuje:  
  
- Przekształcania w formę kanoniczną separatory składnika i katalog.  
  
- Stosowanie bieżący katalog do ścieżki względnej.  
  
- Ocena względna katalogu (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.  
  
- Przycinanie określonych znaków.  
  
## <a name="the-changes"></a>Zmiany  
 Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w następujący sposób:  
  
- Środowisko uruchomieniowe różni się w systemie operacyjnym [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcję, aby znormalizować ścieżki.  
  
- Nie jest już normalizacji obejmuje przycinania koniec segmentów katalogu (np. miejsce na końcu nazwy katalogu).  
  
- Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` a w przypadku plikowych interfejsów API we/wy w mscorlib.dll, `\\?\`.  
  
- Środowisko wykonawcze nie można zweryfikować ścieżki składni urządzeń.  
  
- Użycie składni urządzenia do uzyskania dostępu alternatywne strumienie danych jest obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 W przypadku aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym, te zmiany są domyślnie włączone. One należy poprawić wydajność podczas gdy metody dostępu do ścieżki niedostępnych wcześniej.  
  
 Aplikacje, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i wcześniejszymi wersjami, ale nie są uruchomione w ramach [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszej nie ma wpływu na tę zmianę.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aplikacje, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można zrezygnować z tej zmiany i użyć starszego normalizacji, dodając następujące polecenie, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Aplikacje, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub wcześniej, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji. plik konfiguracji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
