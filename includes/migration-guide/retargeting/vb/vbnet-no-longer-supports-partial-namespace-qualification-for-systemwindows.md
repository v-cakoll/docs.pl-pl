---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804674"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET nie obsługuje już częściowej kwalifikacji obszaru nazw dla interfejsów API systemu.Windows

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5.2 VB.NET projektów nie może określić interfejsów API systemu System.Windows z częściowo kwalifikowanymi obszarami nazw. Na przykład odwoływanie <code>Windows.Forms.DialogResult</code> się do zakończy się niepowodzeniem. Zamiast tego kod musi odwoływać się<xref:System.Windows.Forms.DialogResult>do w pełni kwalifikowanej nazwy <xref:System.Windows.Forms.DialogResult?displayProperty=name>( ) lub importować określony obszar nazw i odnosić się po prostu do .|
|Sugestia|Kod powinien być aktualizowany w celu odwoływania się do <code>System.Windows</code> interfejsów API za pomocą prostych nazw (i importowania odpowiedniego obszaru nazw) lub z w pełni kwalifikowanymi nazwami.|
|Zakres|Mały|
|Wersja|4.5.2|
|Typ|Przekierowanie|
