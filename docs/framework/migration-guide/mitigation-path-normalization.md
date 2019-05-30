---
title: 'Środki zaradcze: Ścieżka normalizacji'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1c704113c8e05e493cdb3ef24f6376ab54b1cb
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251113"
---
# <a name="mitigation-path-normalization"></a>Środki zaradcze: Ścieżka normalizacji
Począwszy od aplikacji docelowej platformy .NET Framework 4.6.2, została zmieniona ścieżka normalizacji w programie .NET Framework.  
  
## <a name="what-is-path-normalization"></a>Co to jest ścieżka normalizacji?  
 Normalizowanie ścieżką obejmuje modyfikuje ciąg, który identyfikuje pliku lub ścieżki, tak aby odpowiada prawidłowej ścieżki, na docelowy system operacyjny. Normalizacja zwykle obejmuje:  
  
- Przekształcania w formę kanoniczną separatory składnika i katalog.  
  
- Stosowanie bieżący katalog do ścieżki względnej.  
  
- Ocena względna katalogu (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.  
  
- Przycinanie określonych znaków.  
  
## <a name="the-changes"></a>Zmiany  
 Począwszy od aplikacji środowiska .NET Framework 4.6.2, zmienił ścieżkę normalizacji w następujący sposób:  
  
- Środowisko uruchomieniowe różni się w systemie operacyjnym [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcję, aby znormalizować ścieżki.  
  
- Nie jest już normalizacji obejmuje przycinania koniec segmentów katalogu (np. miejsce na końcu nazwy katalogu).  
  
- Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` a w przypadku plikowych interfejsów API we/wy w mscorlib.dll, `\\?\`.  
  
- Środowisko wykonawcze nie można zweryfikować ścieżki składni urządzeń.  
  
- Użycie składni urządzenia do uzyskania dostępu alternatywne strumienie danych jest obsługiwane.  
  
## <a name="impact"></a>Wpływ  

W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 lub nowszy, zmiany te są domyślnie włączone. One należy poprawić wydajność podczas gdy metody dostępu do ścieżki niedostępnych wcześniej.  
  
Aplikacje, które przeznaczony dla platformy .NET Framework 4.6.1 oraz wcześniejszymi wersjami, ale działają na platformie .NET Framework 4.6.2 lub nowszej nie ma wpływu na tę zmianę.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aplikacje, które obsługują program .NET Framework 4.6.2 lub nowszej można zrezygnować z tego zmienić i użyć starszego normalizacji, dodając następujące polecenie, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
Aplikacje, których platformą docelową jest program .NET Framework 4.6.1 lub wcześniej, ale są uruchomione w środowisku .NET Framework 4.6.2 lub później włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji plik .configuration aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
