---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616081"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>Obiekt DataObject. GetData teraz pobiera dane jako UTF-8

#### <a name="details"></a>Szczegóły

W przypadku aplikacji przeznaczonych dla .NET Framework 4 lub uruchomionych w .NET Framework 4.5.1 lub wcześniejszych wersjach program `DataObject.GetData` Pobiera dane sformatowane w formacie HTML jako ciąg ASCII. W związku z tym znaki inne niż ASCII (znaki, których kody ASCII są większe niż 0x7F) są reprezentowane przez dwa znaki losowe.<p/>W przypadku aplikacji przeznaczonych dla .NET Framework 4,5 lub nowszych i uruchamianych na .NET Framework 4.5.2 `DataObject.GetData` Pobiera dane sformatowane w formacie HTML jako UTF-8, które reprezentują znaki większe niż 0x7F poprawnie.

#### <a name="suggestion"></a>Sugestia

Jeśli zaimplementowano obejście problemu z kodowaniem w postaci ciągów sformatowanych w formacie HTML (na przykład przez jawne kodowanie ciągu HTML pobranego ze schowka przez przekazanie go do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) i przekierowanie aplikacji z wersji 4 do 4,5, należy usunąć obejście. Jeśli z jakiegoś powodu jest konieczne stare zachowanie, aplikacja może kierować do .NET Framework 4,0, aby uzyskać takie zachowanie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.5.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
