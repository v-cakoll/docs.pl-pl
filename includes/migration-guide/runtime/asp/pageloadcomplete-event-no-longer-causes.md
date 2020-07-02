---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620158"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Zdarzenie Page. LoadComplete nie powoduje już wystąpienia elementu System. Web. UI. WebControls. kontrolka EntityDataSource do wywołania powiązania danych

#### <a name="details"></a>Szczegóły

<xref:System.Web.UI.Page.LoadComplete>Zdarzenie nie powoduje już <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> wywołania powiązania danych dla zmian w celu tworzenia/aktualizowania/usuwania parametrów. Ta zmiana eliminuje niezależną podróż do bazy danych, zapobiega resetowaniu wartości formantów oraz tworzy zachowanie zgodne z innymi kontrolkami danych, takimi jak <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> i <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> . Ta zmiana powoduje inne zachowanie w przypadku, gdy aplikacje są zależne od wywołującego powiązania danych w <xref:System.Web.UI.Page.LoadComplete> zdarzeniu.

#### <a name="suggestion"></a>Sugestia

Jeśli istnieje potrzeba wiązania z danymi, ręcznie Wywołaj wywołanie metody wywołania zwrotnego w zdarzeniu, które jest wcześniej wykonywane po zakończeniu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
