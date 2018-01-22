---
title: 'Porady: zapewnianie pomocy w aplikacji Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d23e5d5d19e17aedd37d4d5f6cbc41429463ddfb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Porady: zapewnianie pomocy w aplikacji Windows
Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika można dołączyć tematów pomocy w pliku pomocy do określonych formantów na formularzach systemu Windows. Może to być plik Pomocy HTML lub HTMLHelp 1.x lub format większa.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-provide-help"></a>Aby zapewnić pomoc  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.HelpProvider> składnika do formularza.  
  
     Składnik będą znajdować się w pasku w dolnej części Projektant formularzy systemu Windows.  
  
2.  W **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości .chm, .col lub .htm pliku pomocy.  
  
3.  Wybierz inny formant na formularzu, a następnie w **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> właściwości.  
  
     Jest to ciąg przekazywane <xref:System.Windows.Forms.HelpProvider> składnika do pliku pomocy wezwać odpowiedniego tematu Pomocy.  
  
4.  W **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> właściwości na wartość <xref:System.Windows.Forms.HelpNavigator> wyliczenia.  
  
     Określa sposób, w którym **HelpKeyword** właściwość jest przekazywana do systemu pomocy. W poniższej tabeli przedstawiono ustawienia możliwe i ich opisy.  
  
    |Nazwa elementu członkowskiego|Opis|  
    |-----------------|-----------------|  
    |AssociateIndex|Określa, czy indeksu dla określonego tematu jest wykonywana w określonym adresem URL.|  
    |Znajdź|Określa, czy są wyświetlane na stronie wyszukiwania określonego adresu URL.|  
    |Indeks|Określa, czy jest wyświetlany indeks określonego adresu URL.|  
    |KeywordIndex|Określa słowo kluczowe do wyszukania i działanie podejmowane w określonym adresem URL.|  
    |TableOfContents|Określa, czy jest wyświetlany tabeli zawartość pliku Pomocy HTML 1.0.|  
    |Temat|Określa, czy temat odwołuje się określony adres URL jest wyświetlana.|  
  
 W czasie wykonywania, naciskając klawisz F1 podczas kontroli — dla którego ustawiono **HelpKeyword** i **HelpNavigator** właściwości — ma fokus zostanie otwarty plik pomocy skojarzony z tym <xref:System.Windows.Forms.HelpProvider> składnika.  
  
 Obecnie **HelpNamespace** właściwość obsługuje pliki pomocy w trzech następujących formatów: HTMLHelp 1.x, HTMLHelp 2.0 i HTML. W związku z tym można ustawić **HelpNamespace** właściwości adresu http://, takich jak strony sieci Web. Jeśli zostanie to zrobione, zostanie otwarty w domyślnej przeglądarce strony sieci Web z określonym w ciągu **HelpKeyword** właściwość używana jako swojej kotwicy. Zakotwiczenia umożliwia przejście do określonej części strony HTML.  
  
> [!IMPORTANT]
>  Należy zachować ostrożność sprawdzić wszystkie informacje, które są wysyłane przez klienta przed jego użyciem w aplikacji. Złośliwi użytkownicy mogą próbować wysyłać lub Wstaw skrypt pliku wykonywalnego, instrukcji SQL lub inny kod. Przed wyświetlania danych wprowadzonych przez użytkownika, zapisz go w bazie danych lub pracę z nią, należy sprawdzić, czy nie zawiera informacji potencjalnie niebezpieczne. Typowym sposobem, aby sprawdzić, jest użycie wyrażenia regularnego wyszukiwanie słów kluczowych "Skrypt" podczas odbierania danych wejściowych od użytkownika.  
  
 Można również użyć <xref:System.Windows.Forms.HelpProvider> składnik, aby wyświetlić Pomoc wyskakująca, nawet jeśli jest ona skonfigurowana do wyświetlania plików pomocy dla formantów na formularzach systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie wyskakujących pomocy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wyświetlanie pomocy podręcznej](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [Pomoc do kontrolek przy użyciu etykietek narzędzi](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrowanie pomocy użytkownika z formularzami Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
