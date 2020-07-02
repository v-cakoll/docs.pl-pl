---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617182"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Metody MachineKey. Encode i MachineKey. Decode są obecnie przestarzałe

#### <a name="details"></a>Szczegóły

Te metody są już nieaktualne. Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.

#### <a name="suggestion"></a>Sugestia

Zalecane alternatywy to <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> . Alternatywnie można pominąć ostrzeżenia kompilacji lub uniknąć ich przy użyciu starszego kompilatora. Interfejsy API są nadal obsługiwane.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
