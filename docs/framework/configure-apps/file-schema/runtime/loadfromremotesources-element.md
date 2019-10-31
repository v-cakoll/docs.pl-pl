---
title: <loadFromRemoteSources> Element
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a4dbcd0a0b848e5ef57965b5b3f4fcee9161b724
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116567"
---
# <a name="loadfromremotesources-element"></a>\<element > loadFromRemoteSources
Określa, czy zestawy ładowane ze źródeł zdalnych powinny mieć przyznane pełne zaufanie w .NET Framework 4 i nowszych.
  
> [!NOTE]
> Jeśli nastąpiło przekierowanie do tego artykułu ze względu na komunikat o błędzie na liście błędów projektu programu Visual Studio lub błąd kompilacji, zobacz [How to: use a Assembly from a Web w Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy zestaw, który jest ładowany ze źródła zdalnego, powinien mieć przyznane pełne zaufanie.|  
  
## <a name="enabled-attribute"></a>włączony atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie należy przyznawać pełnego zaufania do aplikacji ze źródeł zdalnych. Domyślnie włączone.|  
|`true`|Przyznaj pełne zaufanie do aplikacji ze źródeł zdalnych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi

W .NET Framework 3,5 i starszych wersjach, Jeśli ładujesz zestaw z lokalizacji zdalnej, kod w zestawie jest uruchamiany w częściowej relacji zaufania z zestawem uprawnień, który zależy od strefy, z której jest załadowana. Na przykład, Jeśli ładujesz zestaw z witryny sieci Web, zostanie on załadowany do strefy Internet i przyznany zestaw uprawnień internetowych. Innymi słowy, jest wykonywana w piaskownicy internetowej.

Począwszy od .NET Framework 4, zasady zabezpieczeń dostępu kodu (CAS) są wyłączone, a zestawy są ładowane w trybie pełnego zaufania. Zwykle pozwala to na pełne zaufanie do zestawów ładowanych przy użyciu metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, która wcześniej była w trybie piaskownicy. Aby tego uniknąć, możliwość uruchamiania kodu w zestawach załadowanych ze zdalnego źródła jest domyślnie wyłączona. Domyślnie, jeśli próbujesz załadować zestaw zdalny, zostanie zgłoszony <xref:System.IO.FileLoadException> z komunikatem o wyjątku podobnym do następującego:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Aby załadować zestaw i wykonać jego kod, musisz:

- Jawnie Utwórz piaskownicę zestawu (zobacz [jak: uruchamianie częściowo zaufanego kodu w piaskownicy](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Uruchom kod zestawu w trybie pełnego zaufania. W tym celu należy skonfigurować element `<loadFromRemoteSources>`. Pozwala określić, że zestawy, które działają w częściowej relacji zaufania we wcześniejszych wersjach .NET Framework, są teraz uruchamiane w trybie pełnego zaufania w .NET Framework 4 i nowszych wersjach.

> [!IMPORTANT]
> Jeśli zestaw nie powinien działać w trybie pełnego zaufania, nie ustawiaj tego elementu konfiguracji. Zamiast tego należy utworzyć <xref:System.AppDomain> w trybie piaskownicy, w którym ma zostać załadowany zestaw.

Atrybut `enabled` dla elementu `<loadFromRemoteSources>` jest efektywny tylko wtedy, gdy zabezpieczenia dostępu kodu (CAS) są wyłączone. Domyślnie zasady CAS są wyłączone w .NET Framework 4 i nowszych wersjach. Jeśli ustawisz `enabled` na `true`, zdalne zestawy mają przyznane pełne zaufanie.

Jeśli `enabled` nie jest ustawiona na `true`, zostanie zgłoszony <xref:System.IO.FileLoadException> w ramach jednego z następujących warunków:

- Zachowanie w piaskownicy bieżącej domeny różni się od zachowania w .NET Framework 3,5. Wymaga to wyłączenia zasad CAS i bieżącej domeny nie należy do piaskownicy.

- Ładowany zestaw nie należy do strefy `MyComputer`.

Ustawienie elementu `<loadFromRemoteSources>` na `true` uniemożliwia wyrzucanie tego wyjątku. Pozwala to określić, że nie korzystasz z aparatu plików wykonywalnych języka wspólnego do piaskownicy załadowanych zestawów pod kątem zabezpieczeń, i że mogą one być wykonywane w trybie pełnego zaufania.

## <a name="notes"></a>Uwagi

- W .NET Framework 4,5 i nowszych wersjach zestawy w lokalnych udziałach sieciowych są domyślnie uruchamiane w trybie pełnego zaufania; nie musisz włączać elementu `<loadFromRemoteSources>`.

- Jeśli aplikacja została skopiowana z sieci Web, jest oflagowana przez system Windows jako aplikacja sieci Web, nawet jeśli znajduje się na komputerze lokalnym. Można zmienić to oznaczenie poprzez zmianę jego właściwości pliku lub użyć elementu `<loadFromRemoteSources>`, aby nadać zestawowi pełne zaufanie. Alternatywnie można użyć metody <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> do załadowania lokalnego zestawu, który został oflagowany przez system operacyjny jako załadowany z sieci Web.

- Możesz uzyskać <xref:System.IO.FileLoadException> w aplikacji działającej w aplikacji na komputerze wirtualnym z systemem Windows. Taka sytuacja może wystąpić podczas próby załadowania pliku z folderów połączonych na komputerze hostującym. Może również wystąpić podczas próby załadowania pliku z folderu połączonego za pośrednictwem [usługi pulpitu zdalnego](https://go.microsoft.com/fwlink/?LinkId=182775) (usługi terminalowe). Aby uniknąć wyjątku, należy ustawić `enabled` na `true`.

## <a name="configuration-file"></a>Plik konfiguracji

Ten element jest zazwyczaj używany w pliku konfiguracyjnym aplikacji, ale może być używany w innych plikach konfiguracji w zależności od kontekstu. Aby uzyskać więcej informacji, zobacz artykuł [bardziej niejawne zastosowania zasad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) w blogu dotyczącym zabezpieczeń programu .NET.  

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak udzielić pełnego zaufania do zestawów ładowanych ze źródeł zdalnych.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Zobacz także

- [Bardziej niejawne zastosowania zasad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Instrukcje: uruchamianie częściowo zaufanego kodu w piaskownicy](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
