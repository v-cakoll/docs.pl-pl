---
title: <loadFromRemoteSources>, element
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154065"
---
# <a name="loadfromremotesources-element"></a>\<element> loadFromRemoteSources
Określa, czy zestawy ładowane ze źródeł zdalnych powinny mieć pełne zaufanie do programu .NET Framework 4 i nowszych.
  
> [!NOTE]
> Jeśli zostałeś przekierowany do tego artykułu z powodu komunikatu o błędzie na liście błędów projektu programu Visual Studio lub błędu kompilacji, zobacz [Jak: Użyj zestawu z sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy zestaw, który jest ładowany ze źródła zdalnego powinny mieć pełne zaufanie.|  
  
## <a name="enabled-attribute"></a>włączony atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie udzielaj pełnego zaufania do aplikacji ze źródeł zdalnych. Domyślnie włączone.|  
|`true`|Zapewnij pełne zaufanie aplikacjom ze źródeł zdalnych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi

W .NET Framework 3.5 i wcześniejszych wersjach, jeśli załadować zestaw z lokalizacji zdalnej, kod w zestawie działa w częściowym zaufaniu z zestawem dotacji, który zależy od strefy, z której jest ładowany. Na przykład jeśli załadować zestaw z witryny sieci Web, jest ładowany do strefy Internet i przyznane zestaw uprawnień Internet. Innymi słowy, jest on wykonywany w piaskownicy internetowej.

Począwszy od .NET Framework 4, zasady zabezpieczeń dostępu do kodu (CAS) jest wyłączona i zestawy są ładowane w pełnym zaufaniu. Zwykle dałoby to pełne zaufanie do zestawów <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> załadowanych metodą, która wcześniej była w trybie piaskownicy. Aby temu zapobiec, możliwość uruchamiania kodu w zestawach załadowanych ze źródła zdalnego jest domyślnie wyłączona. Domyślnie, jeśli spróbujesz załadować <xref:System.IO.FileLoadException> zestaw zdalny, zostanie wyświetlony komunikat o wyjątku, następujący:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

Aby załadować zestaw i wykonać jego kod, należy:

- Jawnie utworzyć piaskownicę dla zestawu (zobacz [Jak: Uruchom częściowo zaufany kod w piaskownicy](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Uruchom kod zestawu w pełnym zaufaniu. Można to zrobić, `<loadFromRemoteSources>` konfigurując element. Umożliwia określenie, że zestawy, które są uruchamiane w częściowym zaufaniu we wcześniejszych wersjach programu .NET Framework, są teraz uruchamiane w pełnym zaufaniu w programach .NET Framework 4 i nowszych wersjach.

> [!IMPORTANT]
> Jeśli zestaw nie powinien być uruchamiany w pełnym zaufaniu, nie należy ustawiać tego elementu konfiguracji. Zamiast tego należy utworzyć <xref:System.AppDomain> piaskownicy, w którym mają być ładowane złożenia.

Atrybut `enabled` `<loadFromRemoteSources>` elementu jest skuteczny tylko wtedy, gdy zabezpieczenia dostępu do kodu (CAS) jest wyłączona. Domyślnie zasady CAS są wyłączone w .NET Framework 4 i nowszych wersjach. Jeśli ustawisz, `enabled` `true`zestawy zdalne są przyznawane pełne zaufanie.

Jeśli `enabled` nie jest `true`ustawiona na , a <xref:System.IO.FileLoadException> jest wyrzucany pod jednym z następujących warunków:

- Zachowanie piaskownicy bieżącej domeny różni się od jego zachowania w .NET Framework 3.5. Wymaga to wyłączenia zasad CAS, a bieżąca domena nie jest piaskownicy.

- Załadowany zestaw nie pochodzi `MyComputer` ze strefy.

Ustawienie `<loadFromRemoteSources>` elementu, `true` aby zapobiec ten wyjątek z zgłaszanych. Umożliwia określenie, że nie są zależne od środowiska wykonawczego języka wspólnego do piaskownicy załadowanych zestawów dla zabezpieczeń i że mogą one być dozwolone do wykonywania w pełnym zaufaniu.

## <a name="notes"></a>Uwagi

- W .NET Framework 4.5 i nowszych wersjach zestawy w lokalnych udziałach sieciowych są domyślnie uruchamiane w pełnym zaufaniu; nie trzeba włączać `<loadFromRemoteSources>` elementu.

- Jeśli aplikacja została skopiowana z sieci Web, jest oflagowana przez system Windows jako aplikacja sieci web, nawet jeśli znajduje się na komputerze lokalnym. Można zmienić to oznaczenie, zmieniając jego właściwości `<loadFromRemoteSources>` pliku lub można użyć elementu do przyznania pełnego zaufania zestawu. Alternatywnie można użyć <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metody, aby załadować zestaw lokalny, który system operacyjny oflagował jako załadowany z sieci Web.

- Możesz uzyskać <xref:System.IO.FileLoadException> w aplikacji, która jest uruchomiona w aplikacji Windows Virtual PC. Może się to zdarzyć podczas próby załadowania pliku z połączonych folderów na komputerze hostingowym. Może również wystąpić podczas próby załadowania pliku z folderu połączonego za pomocą [usług pulpitu zdalnego](/windows/win32/termserv/terminal-services-portal) (usług terminalowych). Aby uniknąć wyjątku, ustaw `enabled` na `true`.

## <a name="configuration-file"></a>Plik konfiguracji

Ten element jest zwykle używany w pliku konfiguracji aplikacji, ale może być używany w innych plikach konfiguracyjnych w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz artykuł [Więcej niejawnych zastosowań zasad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) w blogu .NET Security.  

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak udzielić pełnego zaufania do zestawów załadowanych ze źródeł zdalnych.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Zobacz też

- [Więcej niejawnych zastosowań zasad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [Porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
