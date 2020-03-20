---
title: 'Łagodzenie: Normalizacja ścieżki'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181235"
---
# <a name="mitigation-path-normalization"></a>Łagodzenie: Normalizacja ścieżki
Począwszy od aplikacji docelowego .NET Framework 4.6.2, normalizacji ścieżki w .NET Framework została zmieniona.  
  
## <a name="what-is-path-normalization"></a>Co to jest normalizacja ścieżki?  
 Normalizacja ścieżki polega na zmodyfikowaniu ciągu identyfikującego ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym. Normalizacja zazwyczaj obejmuje:  
  
- Kanonizacja separatorów komponentów i katalogów.  
  
- Stosowanie bieżącego katalogu do ścieżki względnej.  
  
- Ocena katalogu względnego`.`( ) lub katalogu`..`nadrzędnego ( ) w ścieżce.  
  
- Przycinanie określonych znaków.  
  
## <a name="the-changes"></a>Zmiany  
 Począwszy od aplikacji docelowych dla programu .NET Framework 4.6.2, normalizacja ścieżki zmieniła się w następujący sposób:  
  
- Środowisko wykonawcze defers do systemu operacyjnego [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcji do normalizacji ścieżek.  
  
- Normalizacja nie obejmuje już przycinania końca segmentów katalogów (na przykład spacji na końcu nazwy katalogu).  
  
- Obsługa składni ścieżki urządzenia w pełnym `\\.\` zaufaniu, w tym i dla interfejsów API we/wy pliku w pliku mscorlib.dll, `\\?\`.  
  
- Środowisko wykonawcze nie sprawdza poprawności ścieżek składni urządzenia.  
  
- Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.  
  
## <a name="impact"></a>Wpływ  

W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.6.2 lub nowszego te zmiany są domyślnie włączone. Powinny one poprawić wydajność, umożliwiając jednocześnie metody dostępu wcześniej niedostępne ścieżki.  
  
Aplikacje przeznaczone dla programu .NET Framework 4.6.1 i wcześniejszych wersji, ale są uruchomione w ramach .NET Framework 4.6.2 lub nowszej, nie mają wpływu na tę zmianę.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Aplikacje przeznaczone dla programu .NET Framework 4.6.2 lub nowszego mogą zrezygnować z tej zmiany i używać normalizacji starszych, dodając następujące elementy do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
Aplikacje przeznaczone dla programu .NET Framework 4.6.1 lub starsze, ale działające w programie .NET Framework 4.6.2 lub nowszym, mogą włączyć zmiany w normalizacji ścieżki, dodając następujący wiersz do sekcji>środowiska [ \<wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
