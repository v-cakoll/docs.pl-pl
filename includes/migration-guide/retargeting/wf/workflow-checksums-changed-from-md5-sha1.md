---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859162"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Zmieniono sumę kontrolną przepływu pracy z MD5 na SHA1

|   |   |
|---|---|
|Szczegóły|Aby obsługiwać debugowanie za pomocą programu Visual Studio, środowisko wykonawcze przepływu pracy generuje sumę kontrolną dla wystąpienia przepływu pracy przy użyciu algorytmu mieszania. W .NET Framework 4.6.2 i wcześniejszych wersjach mieszanie sumy kontrolnej przepływu pracy używało algorytmu MD5, który powodował problemy w systemach obsługujących FIPS. Począwszy od .NET Framework 4.7, algorytm jest SHA1. Jeśli kod utrwalił te sumy kontrolne, będą one niezgodne.|
|Sugestia|Jeśli kod nie może załadować wystąpień przepływu pracy z powodu <code>AppContext</code> &quot;błędu sumy kontrolnej, spróbuj użyć true switch.System.Activities.UseMD5ForWFDebugger.&quot; W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Lub w konfiguracji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Przekierowanie|
