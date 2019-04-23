---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774445"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Metody MachineKey.Encode i MachineKey.Decode są obecnie przestarzałe

|   |   |
|---|---|
|Szczegóły|Te metody są już nieaktualne. Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.|
|Sugestia|Zalecanymi alternatywami są <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternatywnie można pominąć ostrzeżenia kompilacji lub można uniknąć za pomocą starszego kompilatora. Interfejsy API są nadal obsługiwane.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
