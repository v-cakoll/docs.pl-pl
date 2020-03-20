---
ms.openlocfilehash: e39b4e85b47902babac7a22a93aa64c2f86ef01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804635"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData pobiera teraz dane jako UTF-8

|   |   |
|---|---|
|Szczegóły|W przypadku aplikacji przeznaczonych dla programu .NET Framework 4 lub uruchomionych w programie <code>DataObject.GetData</code> .NET Framework 4.5.1 lub starszych wersjach pobiera dane w formacie HTML jako ciąg ASCII. W rezultacie znaki inne niż ASCII (znaki, których kody ASCII są większe niż 0x7F) są reprezentowane przez dwa losowe znaki.<p/>W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.5 lub nowszego i <code>DataObject.GetData</code> uruchamianych w programie .NET Framework 4.5.2 dane w formacie HTML są poprawnie wyświetlane w formacie UTF-8, który reprezentuje znaki większe niż 0x7F.|
|Sugestia|Jeśli zaimplementowano obejście problemu z kodowaniem ciągów w formacie HTML (na przykład przez jawne kodowanie ciągu <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>HTML pobranego ze Schowka przez przekazanie go do) i przekierowanie aplikacji z wersji 4 do 4.5, to obejście powinno zostać usunięte. Jeśli stare zachowanie jest potrzebne z jakiegoś powodu, aplikacja może kierować .NET Framework 4.0, aby uzyskać to zachowanie.|
|Zakres|Brzeg|
|Wersja|4.5.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
