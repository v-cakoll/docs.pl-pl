---
title: 'Porady: powiązanie z usługą sieci Web za pomocą formantu BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 5a5db651b0690aae393666124c8d33402d57a189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Porady: powiązanie z usługą sieci Web za pomocą formantu BindingSource formularzy systemu Windows
Jeśli chcesz powiązać kontrolki formularza systemu Windows do wyników uzyskanych z wywoływania usługi XML sieci Web, możesz użyć <xref:System.Windows.Forms.BindingSource> składnika. Ta procedura jest podobna do powiązania <xref:System.Windows.Forms.BindingSource> składnika do typu. Należy utworzyć serwer proxy po stronie klienta, który zawiera metody i typy udostępnianych przez usługę sieci Web. Generowanie jest serwer proxy po stronie klienta z usługi sieci Web (.asmx) samego, lub plik sieci Web Services Description Language (WSDL). Ponadto serwer proxy po stronie klienta musi ujawniać pól złożone typy używane przez usługę sieci Web jako właściwości publiczne. Następnie powiązać <xref:System.Windows.Forms.BindingSource> do jednego z typów udostępniany w sieci Web usługi serwera proxy.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Aby utworzyć i powiązać serwer proxy po stronie klienta  
  
1.  Tworzenie formularza systemu Windows w katalogu wybranych z odpowiedni obszar nazw.  
  
2.  Dodaj <xref:System.Windows.Forms.BindingSource> składnika w formularzu.  
  
3.  Otwórz [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] wiersz polecenia i przejdź do tego samego formularza znajduje się w katalogu.  
  
4.  Za pomocą narzędzia WSDL, wprowadź `wsdl` adres URL pliku WSDL dla usługi sieci Web lub .asmx następuje przestrzeń nazw aplikacji i opcjonalnie język pracujesz w.  
  
     Poniższy przykład kodu wykorzystuje usługę sieci Web w lokalizacji http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx. Na przykład dla typu C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, lub dla języka Visual Basic typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Przekazywanie ścieżkę jako argument do języka WSDL narzędzie wygeneruje serwer proxy po stronie klienta w tym samym katalogu i przestrzeń nazw jako aplikacja w wybranym języku. Jeśli używasz programu Visual Studio, Dodaj plik do projektu.  
  
5.  Wybierz typ serwera proxy po stronie klienta, aby powiązać.  
  
     Zazwyczaj jest to typ zwracany przez metodę oferowane przez usługę sieci Web. Pola wybranego typu musi być udostępniany jako właściwości publiczne dla powiązania celów.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Ustaw <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource> typ ma, który jest zawarty w serwer proxy po stronie klienta usługi sieci Web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Aby powiązać kontrolki BindingSource, który jest powiązany z usługą sieci Web  
  
-   Powiązanie formantów do <xref:System.Windows.Forms.BindingSource>, przekazując właściwość publiczna typu usługi sieci Web, które mają jako parametr.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak można powiązać <xref:System.Windows.Forms.BindingSource> składnik usługi sieci Web, a następnie powiązać pole tekstowe <xref:System.Windows.Forms.BindingSource> składnika. Po kliknięciu przycisku, jest wywoływana metoda usługi sieci Web i wyniki będą wyświetlane w `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jest to pełny przykład, który zawiera `Main` — metoda i skróconej wersji kod po stronie klienta serwera proxy.  
  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing, System.Web.Services, System.Windows.Forms i zestawów System.Xml.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
