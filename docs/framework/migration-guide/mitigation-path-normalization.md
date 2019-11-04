---
title: 'Środki zaradcze: Normalizacja ścieżki'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457884"
---
# <a name="mitigation-path-normalization"></a>Środki zaradcze: Normalizacja ścieżki
Począwszy od aplikacji obiekt docelowy .NET Framework 4.6.2, normalizacja ścieżki w .NET Framework została zmieniona.  
  
## <a name="what-is-path-normalization"></a>Co to jest normalizacja ścieżki?  
 Normalizowanie ścieżki polega na zmodyfikowaniu ciągu, który identyfikuje ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym. Normalizacja zazwyczaj obejmuje:  
  
- Separatory składników formę kanoniczną działa i katalogów.  
  
- Zastosowanie bieżącego katalogu do ścieżki względnej.  
  
- Ocenianie katalogu względnego (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.  
  
- Przycinanie określonych znaków.  
  
## <a name="the-changes"></a>Zmiany  
 Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, normalizacja ścieżki zmieniła się w następujący sposób:  
  
- Środowisko uruchomieniowe odkłada do funkcji [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) systemu operacyjnego, aby znormalizować ścieżki.  
  
- Normalizacja nie obejmuje już przecinania końców segmentów katalogów (takich jak spacja na końcu nazwy katalogu).  
  
- Obsługa składni ścieżki urządzenia w pełnym zaufaniu, w tym `\\.\` i, dla interfejsów API we/wy plików w bibliotece Mscorlib. dll, `\\?\`.  
  
- Środowisko uruchomieniowe nie sprawdza poprawności ścieżek składni urządzeń.  
  
- Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.  
  
## <a name="impact"></a>Wpływ  

W przypadku aplikacji przeznaczonych dla .NET Framework 4.6.2 lub nowszych te zmiany są domyślnie włączone. Powinny one zwiększyć wydajność, jednocześnie umożliwiając metodom dostęp do wcześniej niedostępnych ścieżek.  
  
Ta zmiana nie wpłynie na aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, ale działają na .NET Framework 4.6.2 lub nowszych.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aplikacje przeznaczone dla .NET Framework 4.6.2 lub nowszych mogą zrezygnować z tej zmiany i użyć starszej normalizacji, dodając następujący element do sekcji [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 lub wcześniejszych, ale działają na .NET Framework 4.6.2 lub później, mogą umożliwić zmianę normalizacji ścieżki, dodając następujący wiersz do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) pliku aplikacji. konfiguracji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
