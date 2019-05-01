---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759505"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Sumy kontrolne przepływu pracy, zmienione od MD5, SHA1

|   |   |
|---|---|
|Szczegóły|Aby zapewnić obsługę debugowania programu Visual Studio, środowiska wykonawczego przepływów pracy generuje sumy kontrolnej dla wystąpienia przepływu pracy, przy użyciu algorytmu wyznaczania wartości skrótu. W .NET Framework 4.6.2 i wcześniejszych wersjach przepływ pracy sumy kontrolnej wyznaczania wartości skrótu używany algorytmu MD5, który spowodował problemów w systemach z obsługą standardu FIPS. Począwszy od programu .NET Framework 4.7, algorytm jest algorytm SHA1. Jeśli kod zawiera utrwalone te sumy kontrolne, będą niezgodne.|
|Sugestia|Jeśli Twój kod nie można załadować wystąpienia przepływu pracy z powodu błędu sumy kontrolnej, spróbuj ustawienie <code>AppContext</code> Przełącz &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; na wartość true. W kodzie:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Lub w konfiguracji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Przekierowanie|
