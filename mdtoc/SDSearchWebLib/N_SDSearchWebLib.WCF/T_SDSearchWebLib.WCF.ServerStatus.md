```
@T:SDSearchWebLib.WCF.ServerStatus
```
```csharp
public class ServerStatus
```
```
@M:SDSearchWebLib.WCF.ServerStatus.Echo(System.String)
```
```csharp
[OperationContract]
public string Echo(string inputString)
```
```
@M:SDSearchWebLib.WCF.ServerStatus.GetServerPerformance
```
```csharp
[OperationContract]
[FaultContract(typeof (InvalidUserFaultException))]
public ServerPerformance GetServerPerformance()
```
```
@M:SDSearchWebLib.WCF.ServerStatus.GetUserRequestsBySequenceID(System.Int32)
```
```csharp
[OperationContract]
[FaultContract(typeof (InvalidUserFaultException))]
public UserRequest[] GetUserRequestsBySequenceID(int sequenceID)
```
