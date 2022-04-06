# for_ts
Exercises
For exercises use WebStorm or VSCode or TSPlayground. For WebStorm and VSCode create an empty project and add a .ts file, TypeScript should work out of the box.

From typescript-exercises link
Fork repo https://github.com/typescript-exercises/typescript-exercises/ . How to fork

E1 Interface, Array
E2 Union
E3 Built-in type guards
E4 User-defined type guards
E5 Utility types
E7 Generic, Function, Tuples
E9 Generic
Tasks
Create repo in the GitHub.
Send link to your mentor
For each task create ts file task#.ts.
Task 1
Describe interface User that has the following properties: id, firstName, lastName, isOnline, age, role, address. See usage example below

const user1: User = {
  id: "111",
  firstName: "Ivan",
  lastName: "Ivanov",
  isOnline: false,
  age: 20,
  role: "user",
  address: {
    city: "Minsk",
    country: "Belarus",
    zip: "220000",
  },
};

const user2: User = {
  id: "222",
  firstName: "Ivan",
  lastName: "Ivanov",
  isOnline: false,
  age: 20,
  role: "user",
  address: null,
};

const user3 = {
  id: "333",
  firstName: "Ivan",
  lastName: "Ivanov",
  isOnline: false,
  role: "user",
  address: null,
};
Task 2
Define the following types Role (use enum), Feature (use union), Permissions, FeaturePermission. Available roles are guest, user, and admin. Available features are catalog, basket, news, report. Available permissions are NO_ACCESS , READ, READ_WRITE. For type FeaturePermission use utility types Record and Partial.

// TODO: define Role, Feature, Permission and FeaturePermission

let role: Role = Role.Guest;

let feature: Feature = "catalog";
let permission: Permission = "READ";
const permissions: FeaturePermission = {
  guest: {
    catalog: "READ",
    news: "READ",
  },
  user: {
    catalog: "READ",
    basket: "READ_WRITE",
    news: "READ",
  },
  admin: {
    catalog: "READ_WRITE",
    news: "READ",
    report: "READ",
  },
};
Task 3
Type function hasPermission. See example for more details

function hasAccess(user, features) {
  const role = user.role;
  const rolePermissions = permissions[role];
  const featuresToCheck = Array.isArray(features) ? features : [features];
  return featuresToCheck.every((feature) =>
    ["READ", "READ_WRITE"].includes(rolePermissions[feature])
  );
}

const hasAccessToCatalog = hasAccess(user, "catalog");
const hasAccessToCatalogAndBasket = hasAccess(user, ["basket", "catalog"]);
Task 4
Type function updateUser. See js example for more details below.

function updateUser(user, newValues) {
  return { ...user, ...newValues };
}

const updatedUser = updateUser(user, { isOnline: true });
const updatedUser2 = updateUser(user, { age: 25, lastName: "Petrov" });
Task 5
Type function useState. See source code for more details

function useState(initialValue) {
  let currentValue = initialValue;
  const setValue = (value) => {
    currentValue = value;
  };
  const getValue = () => currentValue;
  return [getValue, setValue, initialValue];
}

const [getValue, setValue, initialValue] = useState(10);
const v = getValue();
setValue(20);
Task 6
Create interface Array with following arrays method: pop, push, sort, indexOf, every, map, filter, reduce. Use javascript docs as references. link Example for slice method

interface Array<T> {
  slice(start?: number, end?: number): T[];
}
  
