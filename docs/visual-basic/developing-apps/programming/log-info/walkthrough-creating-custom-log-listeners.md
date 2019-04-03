---
title: Tworzenie odbiorników logu niestandardowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: c38b6d227859a962c320a0fb2f059294ccacfcfb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831928"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>Przewodnik: Tworzenie odbiorników logu niestandardowego (Visual Basic)
W tym instruktażu pokazano, jak tworzenie odbiorników logu niestandardowego i jest skonfigurowana do nasłuchiwania z danymi wyjściowymi `My.Application.Log` obiektu.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Odbiorniki logu musi dziedziczyć <xref:System.Diagnostics.TraceListener> klasy.  
  
#### <a name="to-create-the-listener"></a>Aby utworzyć odbiornik  
  
-   W aplikacji, należy utworzyć klasę o nazwie `SimpleListener` tej, która dziedziczy <xref:System.Diagnostics.TraceListener>.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> wywołania metody, wymagane przez klasę bazową `MsgBox` wyświetlić ich dane wejściowe.  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Atrybut jest stosowany do <xref:System.Diagnostics.TraceListener.Write%2A> i <xref:System.Diagnostics.TraceListener.WriteLine%2A> metody, aby ich atrybutów pasują do metod klasy bazowej. <xref:System.Security.Permissions.HostProtectionAttribute> Atrybut umożliwia hosta, który jest uruchamiany kod w celu określenia, czy kod przedstawia synchronizacji ochrony hosta.  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> Atrybut obowiązuje tylko w przypadku niezarządzanych aplikacji, które hostują środowisko uruchomieniowe języka wspólnego i implementują ochrony hosta, takie jak SQL Server.  
  
 Aby upewnić się, że `My.Application.Log` korzysta z odbiornikiem dziennika należy jednoznacznie nazwę zestawu, który zawiera Twoje odbiornika dziennika.  
  
 Następna procedura oferuje kilka prostych kroków tworzenia zestawu o silnej nazwie odbiornika dziennika. Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Zdecydowanie nazwy zestawu odbiornika dziennika  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz **właściwości**.   
  
2.  Kliknij przycisk **podpisywanie** kartę.  
  
3.  Wybierz **Podpisz zestaw** pole.  
  
4.  Wybierz  **\<nowy >** z **wybierz plik klucza o silnej nazwie** listy rozwijanej.  
  
     **Utwórz klucz silnej nazwy** zostanie otwarte okno dialogowe.  
  
5.  Podaj nazwę pliku klucza w **nazwę pliku klucza** pole.  
  
6.  Wprowadź hasło w **wprowadź hasło** i **Potwierdź hasło** pola.  
  
7.  Kliknij przycisk **OK**.  
  
8.  Ponownie skompiluj aplikację.  
  
## <a name="adding-the-listener"></a>Dodanie detektora  
 Teraz, że zestaw ma silną nazwą, należy określić silną nazwę odbiornika tak, aby `My.Application.Log` korzysta z odbiornikiem dziennika.  
  
 Format typu o silnej nazwie jest w następujący sposób.  
  
 \<Nazwa typu >, \<Nazwa zestawu >, \<numer wersji >, \<kultury >, \<silnej nazwy >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Aby określić silną nazwę odbiornika  
  
-   Poniższy kod przedstawia sposób określić nazwę typu o silnej nazwie `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Silnej nazwy typu zależy od projektu.  
  
 Za pomocą silnej nazwy, można dodawać przez odbiornik `My.Application.Log` kolekcji odbiornika dziennika.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Aby dodać odbiornika do My.Application.Log  
  
1.  Kliknij prawym przyciskiem myszy w pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     —lub—  
  
     W przypadku pliku app.config:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajdujący się w `<sources>` sekcji. `<sources>` Sekcji znajduje się w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
3.  Dodaj ten element, aby `<listeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Zmień wartość właściwości `SimpleLogStrongName` silną nazwę odbiornika.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Rejestruje wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Instrukcje: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
