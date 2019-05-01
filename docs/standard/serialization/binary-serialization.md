---
title: Serializacja binarna
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 81d79ec0add7f8b73cced5c64a470fa9d699063c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776054"
---
# <a name="binary-serialization"></a>Serializacja binarna

Serializacja mogą być definiowane jako proces przechowywania stanu obiektu na nośniku. W trakcie tego procesu publiczny i prywatny pola obiektu oraz nazwę klasy, łącznie z zestawu zawierającego klasy, są konwertowane na strumień bajtów, które są następnie zapisywane do strumienia danych. Gdy obiekt jest następnie przeprowadzona, dokładną oryginalnego obiektu zostanie utworzony.

Podczas wykonywania mechanizm serializacji w środowisku zorientowane obiektowo, należy wykonać liczbę wpływ na łatwość użycia i elastyczność. Ten proces można automatycznego w dużym stopniu, pod warunkiem, że podane są wystarczające kontrolę nad procesem. Na przykład może przypadki gdzie prosty Serializacja binarna nie jest wystarczająca lub może być określony Przyczyna podjęcie decyzji, które pola w klasie musi być serializowana. Poniższe sekcje bada ten mechanizm serializacji niezawodną udostępniane przy użyciu platformy .NET i zaznacz wiele ważnych funkcji, które umożliwiają dostosowanie procesu do swoich potrzeb.

> [!NOTE]
> Stan UTF-8 lub UTF-7 kodowany obiektu nie jest zachowana, jeśli obiekt jest serializacji i deserializacji za pomocą różnych wersji programu .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Jak charakter serializacji binarnej pozwala na modyfikowanie prywatnych elementów członkowskich wewnątrz obiektu i w związku z tym zmiana stanu go, zaleca się środowisk innych serializacji, takich jak program JSON.NET działających na publicznych powierzchni interfejsu API.

## <a name="binary-serialization-in-net-core"></a>Serializacja binarna w programie .NET Core

Program .NET core obsługuje serializacji binarnej z podzbioru typów. Można wyświetlić listę obsługiwanych typów w [sekcja: typy możliwe do serializacji](#serializable-types). Określony zbiór typów zapewniona jest możliwy do serializacji między .NET Framework 4.5.1 i nowsze wersje i .NET Core 2.0 i nowszych wersjach. Inne implementacje platformy .NET, takich jak platformy Mono, oficjalnie nie są obsługiwane, ale również powinny działać.

### <a name="serializable-types"></a>Typy z możliwością serializowania

- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.AccessViolationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.AggregateException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ApplicationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ArgumentException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ArgumentNullException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ArithmeticException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Array?displayProperty=nameWithType>
- <xref:System.ArraySegment%601?displayProperty=nameWithType>
- <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.BadImageFormatException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Boolean?displayProperty=nameWithType>
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>
- <xref:System.Collections.BitArray?displayProperty=nameWithType>
- <xref:System.Collections.Comparer?displayProperty=nameWithType>
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.Queue?displayProperty=nameWithType>
- <xref:System.Collections.SortedList?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Stack?displayProperty=nameWithType>
- `System.Collections.Generic.NonRandomizedStringEqualityComparer` (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 i nowszych wersjach, serializacji z .NET Framework i .NET Core nie jest obsługiwany)
- <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ContextMarshalException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DBNull?displayProperty=nameWithType> (dostępne w .NET Core pkt 2.0.2 i nowsze wersje)
- <xref:System.Data.Common.DbException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.ConstraintException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.DataException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.DataSet?displayProperty=nameWithType>
- <xref:System.Data.DataTable?displayProperty=nameWithType> (o ile nie ustawisz RemotingFormat SerializationFormat.Binary w takim przypadku go tylko uniemożliwiającym wymienianie przy użyciu platformy .NET Core 2.1 i nowsze wersje.)
- <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.EvaluateException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>
- <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 i nowszych wersjach, serializacji z .NET Framework i .NET Core nie jest obsługiwany)
- <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.StrongTypingException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DataMisalignedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- `System.Diagnostics.Contracts.ContractException` (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DivideByZeroException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.DllNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Drawing.Color?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- <xref:System.Drawing.PointF?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>
- <xref:System.Drawing.Size?displayProperty=nameWithType>
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>
- <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.EventArgs?displayProperty=nameWithType> (dostępne w .NET Core 2.0.6 i nowsze wersje)
- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.ExecutionEngineException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.FieldAccessException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.FormatException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>
- <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- `System.IO.Compression.ZLibException` (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.FileFormatException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.FileLoadException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.IOException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.InvalidDataException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.InsufficientMemoryException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IntPtr?displayProperty=nameWithType>
- <xref:System.InvalidCastException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.InvalidOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.InvalidProgramException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MemberAccessException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MethodAccessException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MissingFieldException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MissingMemberException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MissingMethodException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.Cookie?displayProperty=nameWithType>
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>
- <xref:System.Net.CookieException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.HttpListenerException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.WebException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.NotFiniteNumberException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.NotImplementedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.NotSupportedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.NullReferenceException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.ObjectDisposedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.OperationCanceledException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.OutOfMemoryException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.OverflowException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.RankException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 i nowszych wersjach, serializacji z .NET Framework i .NET Core nie jest obsługiwany)
- <xref:System.Reflection.TargetException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.HostProtectionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.SecurityException?displayProperty=nameWithType> (dostępne w przypadku platformy .NET Core 2.0.4 i nowsze wersje, dane serializacji ograniczony)
- <xref:System.Security.VerificationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.StackOverflowException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.SystemException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>
- <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.TimeoutException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Transactions.TransactionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Tuple?displayProperty=nameWithType>
- <xref:System.TypeAccessException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.TypeInitializationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.TypeLoadException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.TypeUnloadedException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.UIntPtr?displayProperty=nameWithType>
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.UriFormatException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.ValueTuple?displayProperty=nameWithType> (nie można serializować w .NET Framework 4.7 i wcześniejsze wersje)
- <xref:System.ValueType?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:System.WeakReference%601?displayProperty=nameWithType>
- <xref:System.WeakReference?displayProperty=nameWithType>
- <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.XmlException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)
- <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> (dostępne w .NET Core 2.0.4 lub nowszy)

## <a name="in-this-section"></a>W tej sekcji

- [Pojęcia dotyczące serializacji](../../../docs/standard/serialization/serialization-concepts.md)\
Opisano dwa scenariusze, w których jest użyteczny serializacji: Jeśli utrwalanie danych do magazynu i przekazywania obiekty domen aplikacji.

- [Serializacja podstawowa](../../../docs/standard/serialization/basic-serialization.md)\
Opisuje sposób używania PLiku binarnego i SOAP elementy formatujące do wykonywania serializacji obiektów.

- [Serializacja selektywna](../../../docs/standard/serialization/selective-serialization.md)\
Opisuje sposób zapobiegania serializacji niektórych składowych klasy.

- [Niestandardowej serializacji](../../../docs/standard/serialization/custom-serialization.md)\
Opisuje sposób dostosować serializacji dla klasy przy użyciu <xref:System.Runtime.Serialization.ISerializable> interfejsu.

- [Kroki procesu serializacji](../../../docs/standard/serialization/steps-in-the-serialization-process.md)\
Opisuje kurs akcji serializacji przyjmuje, gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda jest wywoływana w elementu formatującego.

- [Serializacja z tolerancją wersji](../../../docs/standard/serialization/version-tolerant-serialization.md)\
Wyjaśnia sposób tworzenia typów możliwych do serializacji, które mogą być modyfikowane bez powodowania aplikacjom zgłaszają wyjątki, wraz z upływem czasu.

- [Wskazówki dotyczące serializacji](../../../docs/standard/serialization/serialization-guidelines.md)\
Zawiera ogólne zasady ustalania, kiedy można serializować obiektu.

## <a name="reference"></a>Tematy pomocy

- <xref:System.Runtime.Serialization>\
Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.

## <a name="related-sections"></a>Sekcje pokrewne

- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)\
Opisuje mechanizm serializacji XML, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)\
Opisuje bezpiecznego wskazówek kodowania, które należy wykonać podczas pisania kodu, który będzie wykonywać serializacji.

- [Wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.

- [Usługi sieci Web XML utworzone za pomocą platformy ASP.NET i klientów usługi sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
Zawiera tematy, które opisują, a wyjaśniają, jak program usług sieci Web XML utworzone za pomocą programu ASP.NET.