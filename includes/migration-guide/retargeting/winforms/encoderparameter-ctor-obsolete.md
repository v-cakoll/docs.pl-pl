---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774411"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor jest przestarzała

|   |   |
|---|---|
|Szczegóły|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor jest obecnie przestarzała i będzie powodować ostrzeżenia kompilacji, jeśli używane.|
|Sugestia|Mimo że <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor będą nadal działać, następujący Konstruktor należy użyć w celu uniknięcia ostrzeżeń kompilacji przestarzałe podczas ponownego kompilowania kodu za pomocą narzędzi programu .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
