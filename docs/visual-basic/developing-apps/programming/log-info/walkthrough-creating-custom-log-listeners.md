---
title: "Tworzenie odbiorników logu niestandardowego (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1bda4a3465af4ed95de720117ea2e03f9a86b84
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)
W tym przewodniku pokazano, jak utworzyć odbiornik dziennik niestandardowy i skonfigurować go do nasłuchiwania na dane wyjściowe `My.Application.Log` obiektu.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Odbiorniki logu musi dziedziczyć z <xref:System.Diagnostics.TraceListener> klasy.  
  
#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik  
  
-   W aplikacji, Utwórz klasę o nazwie `SimpleListener` dziedziczący po <xref:System.Diagnostics.TraceListener>.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> wywołania metody, wymagane przez klasę podstawową `MsgBox` do wyświetlania danych wejściowych.  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Atrybut jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, aby ich atrybutów odpowiadały metod klasy podstawowej. <xref:System.Security.Permissions.HostProtectionAttribute> Atrybutu umożliwia hosta, który uruchamia kod, aby określić, że kod przedstawia synchronizacji ochrony hosta.  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> Atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji, która hostowanie środowiska CLR i implementują ochrony hosta, takich jak SQL Server.  
  
 Aby upewnić się, że `My.Application.Log` używa odbiornika z dziennika, należy silnie nazwę zestawu zawierającego odbiornika z dziennika.  
  
 Następna procedura zawiera kilku prostych czynności tworzenia zestawu o silnej nazwie odbiornika dziennika. Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Silnej nazwy zestawu odbiornika dziennika  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Kliknij przycisk **podpisywanie** kartę.  
  
3.  Wybierz **Podpisz zestaw** pole.  
  
4.  Wybierz  **\<nowy >** z **wybierz plik klucza o silnej nazwie** listy rozwijanej.  
  
     **Tworzenie silnej nazwy klucza** zostanie otwarte okno dialogowe.  
  
5.  Podaj nazwę dla pliku klucza w **nazwę pliku klucza** pole.  
  
6.  Wprowadź hasło w **wprowadź hasło** i **Potwierdź hasło** pola.  
  
7.  Kliknij przycisk **OK**.  
  
8.  Skompiluj ponownie aplikację.  
  
## <a name="adding-the-listener"></a>Dodawanie odbiornika  
 Teraz, gdy zestaw ma silną nazwę, należy określić silne nazwę odbiornika, aby `My.Application.Log` używa odbiornika z dziennika.  
  
 Format typu silną nazwą ma następującą składnię.  
  
 \<Nazwa typu >, \<Nazwa zestawu >, \<numer wersji >, \<kultury >, \<silnej nazwy >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silnej nazwy odbiornika  
  
-   Poniższy kod przedstawia sposób określić nazwę typu o silnej nazwie `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     Silnej nazwy typu zależy od projektu.  
  
 O silnej nazwie, można dodać obiektu nasłuchującego do `My.Application.Log` kolekcji odbiornika dziennika.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornika do My.Application.Log  
  
1.  Kliknij prawym przyciskiem myszy w pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     W przypadku pliku app.config:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajduje się w `<sources>` sekcji. `<sources>` Sekcja znajduje się w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
3.  Ten element, aby dodać `<listeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Zmień wartość `SimpleLogStrongName` silną nazwę odbiornika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Porady: wyjątki rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
