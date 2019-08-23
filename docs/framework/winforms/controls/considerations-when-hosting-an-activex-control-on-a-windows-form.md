---
title: Uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933412"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows
Mimo że Windows Forms zostały zoptymalizowane pod kątem hostów Windows Forms, można nadal korzystać z kontrolek ActiveX. Podczas planowania aplikacji korzystającej z formantów ActiveX należy pamiętać o następujących kwestiach:  
  
- **Zabezpieczenia** Środowisko uruchomieniowe języka wspólnego zostało udoskonalone w odniesieniu do zabezpieczeń dostępu kodu. Aplikacje zawierające Windows Forms mogą działać w w pełni zaufanym środowisku bez problemów i w środowisku częściowo zaufanym z większością dostępnych funkcji. Formanty Windows Forms mogą być hostowane w przeglądarce bez komplikacji. Jednak kontrolki ActiveX na Windows Forms nie mogą korzystać z tych ulepszeń zabezpieczeń. Uruchamianie kontrolki ActiveX wymaga uprawnienia do kodu niezarządzanego, który jest <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> ustawiany z właściwością. Aby uzyskać więcej informacji dotyczących zabezpieczeń i uprawnienia do kodu niezarządzanego, zobacz <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
- **Łączny koszt posiadania** Kontrolki ActiveX dodawane do formularza systemu Windows są wdrażane razem z tym formularzem systemu Windows, co może znacznie zwiększyć rozmiar utworzonych plików. Ponadto Używanie formantów ActiveX w Windows Forms wymaga zapisu w rejestrze. Jest to bardziej inwazyjne dla komputera użytkownika niż kontrolki Windows Forms, które nie wymagają tego.  
  
    > [!NOTE]
    > Praca z kontrolką ActiveX wymaga użycia otoki międzyoperacyjności modelu COM. Aby uzyskać więcej informacji, zobacz Współdziałanie [com w C#Visual Basic i wizualizacji ](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    > Jeśli nazwa elementu członkowskiego kontrolki ActiveX pasuje do nazwy zdefiniowanej w .NET Framework, wówczas importer kontrolki ActiveX będzie poprzedzał nazwę elementu członkowskiego **listą CTL** podczas tworzenia <xref:System.Windows.Forms.AxHost> klasy pochodnej. Na przykład, jeśli formant ActiveX ma element członkowski o nazwie **layout**, jego nazwa zostanie zmieniona na **CtlLayout** w klasie pochodnej AxHost, ponieważ zdarzenie **układu** jest zdefiniowane w .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodaj kontrolki ActiveX do Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Zabezpieczenia dostępu kodu](../../misc/code-access-security.md)
- [Formanty i obiekty programowalne porównane w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Umieszczanie kontrolek na formularzach Windows Forms](putting-controls-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms](index.md)
