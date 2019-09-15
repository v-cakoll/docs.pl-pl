---
title: Tworzenie odbiorników dziennika niestandardowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: a4bd64d4c8232f9b6448baf98ee73ee497ccd5ca
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972107"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Przewodnik: Tworzenie odbiorników dziennika niestandardowego (Visual Basic)
W tym instruktażu pokazano, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych `My.Application.Log` obiektu.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Odbiorniki dzienników muszą dziedziczyć <xref:System.Diagnostics.TraceListener> z klasy.  
  
#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik  
  
- W aplikacji Utwórz klasę o nazwie `SimpleListener` , która dziedziczy z. <xref:System.Diagnostics.TraceListener>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     Metody <xref:System.Diagnostics.TraceListener.Write%2A> `MsgBox` i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , wymagane przez klasę bazową, wywołują, aby wyświetlić ich dane wejściowe.  
  
     Ten atrybut jest stosowany <xref:System.Diagnostics.TraceListener.Write%2A> do metod i <xref:System.Diagnostics.TraceListener.WriteLine%2A> , tak aby ich atrybuty pasowały do metod klasy bazowej. <xref:System.Security.Permissions.HostProtectionAttribute> Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut zezwala na hosta, na którym jest uruchamiany kod, aby określić, że kod uwidacznia synchronizację z ochroną hosta.  
  
    > [!NOTE]
    > Ten <xref:System.Security.Permissions.HostProtectionAttribute> atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji obsługujących środowisko uruchomieniowe języka wspólnego i implementujących ochronę hosta, takich jak SQL Server.  
  
 Aby zapewnić, `My.Application.Log` że program korzysta z odbiornika dzienników, należy silnie nawiązać nazwę zestawu, który zawiera odbiornik dzienników.  
  
 Kolejna procedura zawiera kilka prostych kroków służących do tworzenia silnie nazwanego zestawu detektora dzienników. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](../../../../standard/assembly/create-use-strong-named.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Aby silnie nawiązać nazwę zestawu odbiornika dzienników  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **Właściwości**.   
  
2. Kliknij kartę **podpisywanie** .  
  
3. Zaznacz pole **podpisz zestaw** .  
  
4. Wybierz pozycję  **\<Nowy >** z listy rozwijanej **Wybierz plik klucza o silnej nazwie** .  
  
     Zostanie otwarte okno dialogowe **Tworzenie klucza silnej nazwy** .  
  
5. Podaj nazwę pliku klucza w polu **Nazwa pliku klucza** .  
  
6. Wprowadź hasło w polach **Wprowadź hasło** i **Potwierdź hasło** .  
  
7. Kliknij przycisk **OK**.  
  
8. Skompiluj ponownie aplikację.  
  
## <a name="adding-the-listener"></a>Dodawanie odbiornika  
 Teraz, gdy zestaw ma silną nazwę, należy określić silną nazwę odbiornika, aby `My.Application.Log` używała odbiornika dzienników.  
  
 Format silnie nazwanego typu jest następujący.  
  
 \<Nazwa typu >, \<nazwa zestawu >, \<numer wersji >, \<kultura >, \<silna nazwa >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silną nazwę odbiornika  
  
- Poniższy kod pokazuje, jak określić silną nazwę typu dla `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Silna nazwa typu zależy od projektu.  
  
 Za pomocą silnej nazwy można dodać odbiornik do `My.Application.Log` kolekcji detektorów dzienników.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornik do My. Application. log  
  
1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     Jeśli istnieje plik App. config:  
  
    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.  
  
    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.  
  
    3. Kliknij przycisk **Dodaj**.  
  
2. Znajdź sekcję w sekcji z `name` atrybutem "DefaultSource", który znajduje się w sekcji.`<sources>` `<source>` `<listeners>` Sekcja znajduje się `<system.diagnostics>` w sekcji w sekcji najwyższego poziomu `<configuration>`. `<sources>`  
  
3. Dodaj ten element do `<listeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. `<sharedListeners>` Znajdź sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .  
  
5. Dodaj ten element do tej `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Zmień wartość `SimpleLogStrongName` tak, aby była silną nazwą odbiornika.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Instrukcje: Zapisuj komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
