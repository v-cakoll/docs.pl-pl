---
title: Powiąż z usługą sieci Web przy użyciu źródła BindingSource
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
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746678"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Porady: powiązanie z usługą sieci Web za pomocą kontrolki BindingSource formularzy systemu Windows
Jeśli chcesz powiązać formant formularza systemu Windows z wynikami uzyskanymi z wywołania usługi sieci Web XML, możesz użyć składnika <xref:System.Windows.Forms.BindingSource>. Ta procedura jest podobna do powiązania składnika <xref:System.Windows.Forms.BindingSource> z typem. Należy utworzyć serwer proxy po stronie klienta zawierający metody i typy udostępniane przez usługę sieci Web. Serwer proxy po stronie klienta jest generowany na podstawie samej usługi sieci Web (. asmx) lub pliku Web Services Description Language (WSDL). Ponadto serwer proxy po stronie klienta musi ujawniać pola typów złożonych używanych przez usługę sieci Web jako właściwości publiczne. Następnie można powiązać <xref:System.Windows.Forms.BindingSource> z jednym z typów uwidocznionych w serwerze proxy usługi sieci Web.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Aby utworzyć i powiązać serwer proxy po stronie klienta  
  
1. Utwórz w wybranym katalogu formularz systemu Windows z odpowiednią przestrzenią nazw.  
  
2. Dodaj składnik <xref:System.Windows.Forms.BindingSource> do formularza.  
  
3. Otwórz wiersz polecenia zestawu Windows Software Development Kit (SDK) i przejdź do tego samego katalogu, w którym znajduje się formularz.  
  
4. Za pomocą narzędzia WSDL wprowadź `wsdl` i adres URL pliku. asmx lub WSDL dla usługi sieci Web, a następnie przestrzeń nazw aplikacji i opcjonalnie język, w którym pracujesz.  
  
     Poniższy przykład kodu używa usługi sieci Web znajdującej się w `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Na przykład dla C# typu `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`lub Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`. Przekazanie ścieżki jako argumentu narzędzia WSDL spowoduje wygenerowanie serwera proxy po stronie klienta w tym samym katalogu i przestrzeni nazw, w którym znajduje się aplikacja, w określonym języku. Jeśli używasz programu Visual Studio, Dodaj plik do projektu.  
  
5. Wybierz typ w serwerze proxy po stronie klienta, z którym ma zostać utworzone powiązanie.  
  
     Zwykle jest to typ zwracany przez metodę oferowaną przez usługę sieci Web. Pola wybranego typu muszą być uwidocznione jako właściwości publiczne na potrzeby tworzenia powiązań.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. Ustaw właściwość <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource> na typ, który ma być zawarty w serwerze proxy po stronie klienta usługi sieci Web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Aby powiązać kontrolki ze źródłem BindingSource, które jest powiązane z usługą sieci Web  
  
- Powiązywanie kontrolek z <xref:System.Windows.Forms.BindingSource>, przekazując Właściwość publiczną typu usługi sieci Web, która ma być parametrem.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób powiązania składnika <xref:System.Windows.Forms.BindingSource> z usługą sieci Web, a następnie powiązania pola tekstowego ze składnikiem <xref:System.Windows.Forms.BindingSource>. Po kliknięciu przycisku zostanie wywołana metoda usługi sieci Web, a wyniki pojawią się w `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jest to kompletny przykład, który obejmuje metodę `Main` i skróconą wersję kodu serwera proxy po stronie klienta.  
  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing, system. Web. Services, system. Windows. Forms i system. XML.  
  
## <a name="see-also"></a>Zobacz także

- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
