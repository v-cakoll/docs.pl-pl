---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616074"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET nie obsługuje już częściowego kwalifikowania przestrzeni nazw dla interfejsów API System. Windows

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.5.2, projekty VB.NET nie mogą określać interfejsów API System. Windows z częściowo kwalifikowanymi przestrzeniami nazw. Na przykład odwołanie do `Windows.Forms.DialogResult` nie powiedzie się. Zamiast tego, kod musi odwoływać się do w pełni kwalifikowanej nazwy ( <xref:System.Windows.Forms.DialogResult> ) lub zaimportować określoną przestrzeń nazw i zajrzeć się po prostu do <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .

#### <a name="suggestion"></a>Sugestia

Kod powinien zostać zaktualizowany w celu odwoływania się do `System.Windows` interfejsów API przy użyciu prostych nazw (i importowania odpowiedniej przestrzeni nazw) lub z w pełni kwalifikowanymi nazwami.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5.2       |
| Typ    | Przekierowanie |
