# Global use for React components

The goal for this project is to create a React setup where components which are used more than once are structured in the following way.

```javascript
// Components
import Layout from "./Layout";
import Card from "./Card";
import Text from "./Text";
import Button from "./Button";

const Structure = () => {
  return (
    <Layout __type="container">
      <Card __type="primary">
        <Text __type="h1" primary>
          Global use for React components
        </Text>
        <Button __type="default">Next →</Button>
      </Card>
    </Layout>
  );
};

export default Structure;
```

## How to structure your code this way?

### 1. Create a global component

Is this example I created a component with the name `Card`. This component will receive the a prop with the name `__type` and returns the associated `Card` for this type.

```javascript
// Cards
import DefaultCard from "./DefaultCard";
import SecondaryCard from "./SecondaryCard";
import UserCard from "./UserCard";

const cards = {
  default: DefaultCard,
  secondary: SecondaryCard,
  user: UserCard
};

const Card = ({ __type, ...props }) => {
  const Comp = cards[__type];
  if (typeof cards[__type] === "undefined") {
    return null;
  }
  return Comp && <Comp {...props} />;
};

export default Card;
```
