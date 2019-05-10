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
ms.openlocfilehash: 9b037dfbb3a82b8df4c91468eeb8b2dea24e2a37
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625422"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows
Mimo że formularze Windows zostały zoptymalizowane do kontrolek Windows Forms hosta, ale nadal używać kontrolki ActiveX. Podczas planowania aplikacji korzystającej z formantów ActiveX, należy pamiętać o następujących kwestiach:  
  
- **Zabezpieczenia** w odniesieniu do zabezpieczeń dostępu kodu zostało ulepszone środowisko uruchomieniowe języka wspólnego. Aplikacje Windows Forms z można uruchomić w pełni zaufanym środowisku bez problemu i częściowo zaufanym środowisku z większością funkcji, które są dostępne. Kontrolek formularzy Windows Forms może być hostowana w przeglądarce nie kompilacji. Jednak formantów na formularzach Windows Forms nie może zastosować te ulepszenia zabezpieczeń. Uruchamianie formantu ActiveX wymaga uprawnień kodu niezarządzanego, która została ustawiona za pomocą <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji dotyczących zabezpieczeń i uprawnień do kodu niezarządzanego, zobacz <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
- **Całkowity koszt posiadania** formantów ActiveX dodany do formularza Windows zostały wdrożone za pomocą formularza Windows w całości, która może znacznie wydłużyć rozmiar utworzone pliki. Ponadto za pomocą formantów na formularzach Windows Forms wymaga zapisywania w rejestrze. Jest to bardziej inwazyjne na komputerze użytkownika niż formanty Windows Forms, które nie wymagają tego.  
  
    > [!NOTE]
    >  Praca z ActiveX kontrolki wymaga użycia otokę międzyoperacyjne COM. Aby uzyskać więcej informacji, zobacz [współdziałanie COM w języku Visual Basic i Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  Jeśli nazwa składowej formantu ActiveX pasuje do nazwy zdefiniowanej w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], a następnie Importer formantów ActiveX będzie prefiks nazwy elementu członkowskiego z **Ctl** gdy tworzy <xref:System.Windows.Forms.AxHost> klasy pochodnej. Na przykład, jeśli formant ActiveX ma składową o nazwie **układ**, jej nazwa zostanie zmieniona **CtlLayout** w klasie pochodnej AxHost ponieważ **układ** zdarzeń jest zdefiniowana w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie kontrolek ActiveX do formularzy Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Zabezpieczenia dostępu kodu](../../misc/code-access-security.md)
- [Formantów i programowanych obiektów w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Umieszczanie kontrolek na formularzach Windows Forms](putting-controls-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms](index.md)
