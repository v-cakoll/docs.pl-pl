---
ms.openlocfilehash: 43e9c1c2f03daedf4d56152da5672b89399a3c69
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804674"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET nie obsługuje już kwalifikacji częściowego przestrzeń nazw System.Windows interfejsów API

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.5.2 projektów VB.NET, nie można określić System.Windows interfejsów API przy użyciu częściowo kwalifikowanych przestrzeni nazw. Na przykład, odnoszące się do <code>Windows.Forms.DialogResult</code> zakończy się niepowodzeniem. Zamiast tego kod musi odwoływać się do w pełni kwalifikowana nazwa (<xref:System.Windows.Forms.DialogResult>) lub importowanie określonej przestrzeni nazw i odwoływać się tylko do <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Sugestia|Kod powinien zostać zaktualizowany do odwoływania się do <code>System.Windows</code> interfejsów API przy użyciu prostego nazwy (i importowania odpowiednich przestrzeni nazw) lub za pomocą w pełni kwalifikowanych nazw.|
|Scope|Mały|
|Wersja|4.5.2|
|Typ|Przekierowanie|

