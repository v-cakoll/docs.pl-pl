---
ms.openlocfilehash: c800b3fcc1eff5d7a669611cb0697aa8c87a37a4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804635"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData teraz pobiera dane w formacie UTF-8

|   |   |
|---|---|
|Szczegóły|W przypadku aplikacji, przeznaczone na platformę .NET Framework 4 lub działających w .NET Framework 4.5.1 i jego wcześniejsze wersje <code>DataObject.GetData</code> pobiera dane w formacie HTML jako ciąg znaków ASCII. W rezultacie znaki spoza zestawu ASCII (znaki, których kodów ASCII są większe niż 0x7F) są reprezentowane przez dwa losowo wybranych znaków.<p/>W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.5 lub nowszej i korzystać w środowisku .NET Framework 4.5.2 <code>DataObject.GetData</code> pobiera dane w formacie HTML w formacie UTF-8, który reprezentuje poprawnie znaków jest większa niż 0x7F.|
|Sugestia|Jeśli zaimplementowano obejścia problemu kodowania, za pomocą ciągów w formacie HTML (na przykład przez jawne kodowania ciąg HTML pobierane ze Schowka przez przekazanie jej do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) i masz przekierowania aplikacji za pomocą wersji 4 do 4.5, obejście należy je usunąć. W razie stare zachowanie jest jakiegoś powodu aplikacji mogą określać docelową .NET Framework 4.0 można pobrać tego zachowania.|
|Scope|Krawędź|
|Wersja|4.5.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

